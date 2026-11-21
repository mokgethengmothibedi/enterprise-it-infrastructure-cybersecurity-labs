# Active Directory PowerShell Audit Report

**System audited:** MT-DC01  
**Audit date:** 2026-11-21 (date the report was received; execution timestamp was not included in the supplied output)  
**Domain:** ad.mothibedi.test  
**NetBIOS name:** MOTHIBEDI  
**Audit source:** PowerShell audit output supplied for this portfolio  
**Audit type:** Read-only inventory review

## 1. Executive summary

The domain is established and contains a departmental OU structure, eight enabled employee accounts across four departments, four matching global security groups, two domain computer objects and four departmental file shares.

The current departmental structure includes IT, Finance, HR and Admin. **Management is not present** in the supplied OU, employee-account, security-group or file-share inventories.

The audit also displays an OU with a blank/whitespace-looking name at the domain root. Its exact distinguished name was truncated in the pasted output. This is an anomaly requiring direct inspection before any cleanup.

The audit output is an inventory snapshot. It does not prove that file-share or NTFS permissions are correctly configured, that custom GPOs exist, or that every DNS health test passed.

## 2. Domain information

| Attribute | Observed value |
|---|---|
| DNS domain | ad.mothibedi.test |
| NetBIOS name | MOTHIBEDI |
| Domain distinguished name | DC=ad,DC=mothibedi,DC=test |

## 3. Organisational unit inventory

The following OU names are visible in the supplied output:

| OU | Observed location / notes |
|---|---|
| Domain Controllers | Domain Controllers container OU at domain level |
| Mothibedi Technologies | Top-level organisation OU |
| Departments | Under Mothibedi Technologies |
| Security Groups | Under Mothibedi Technologies |
| Service Accounts | Under Mothibedi Technologies |
| Workstations | Under Mothibedi Technologies |
| Servers | Under Mothibedi Technologies |
| IT | Under Departments |
| Finance | Under Departments |
| HR | Under Departments |
| Admin | Under Departments |
| Blank/whitespace-looking OU | An additional OU row appears with an incomplete/truncated DN; exact name and parent need verification |

### OU observations

- The four departmental OUs currently visible are IT, Finance, HR and Admin.
- No Management OU appears in the supplied OU listing.
- The audit output does not establish whether the blank-looking OU is truly empty, contains objects, or is a formatting/truncation artefact.
- Do not delete, rename or move the anomalous OU until its exact name, DN, child objects and purpose have been inspected.

## 4. User account inventory

Eight enabled employee accounts are visible:

| Department | Display name | SamAccountName | Enabled |
|---|---|---|---|
| IT | Thabo Molefe | it.thabo | Yes |
| IT | Lerato Mokoena | it.lerato | Yes |
| Finance | Kabelo Dlamini | fin.kabelo | Yes |
| Finance | Naledi Nkosi | fin.naledi | Yes |
| HR | Sipho Khumalo | hr.sipho | Yes |
| HR | Palesa Ndlovu | hr.palesa | Yes |
| Admin | Musa Maseko | admin.musa | Yes |
| Admin | Zanele Sithole | admin.zanele | Yes |

Built-in accounts also listed include Administrator (enabled), Guest (disabled) and krbtgt (disabled). These are not departmental employee accounts.

### Account observations

- Two employee accounts are present in each of the four listed departments.
- No Management employee account appears in the supplied inventory.
- The output shows employee accounts located under their corresponding departmental OUs.
- No password values or password-policy settings were included in the report; no conclusions about password security can be drawn from this inventory.

## 5. Security group inventory and membership

Four custom global security groups are visible:

| Group | Scope | Category | Observed members |
|---|---|---|---|
| GG_IT_Users | Global | Security | it.thabo, it.lerato |
| GG_Finance_Users | Global | Security | fin.kabelo, fin.naledi |
| GG_HR_Users | Global | Security | hr.sipho, hr.palesa |
| GG_Admin_Users | Global | Security | admin.musa, admin.zanele |

The output also lists standard built-in/domain groups. The four custom groups have memberships aligned with the four departmental user pairs in the audit.

### Group observations

- No GG_Management_Users group appears in the supplied group inventory.
- The audit does not show a Management membership assignment.
- Membership alignment is visible for the four existing departments; resource permissions and effective access still need separate testing.

## 6. Computer objects

| Computer | Enabled | Observed location |
|---|---|---|
| MT-DC01 | Yes | OU=Domain Controllers |
| MT-WS01 | Yes | CN=Computers,DC=ad,DC=mothibedi,DC=test |

MT-WS01 is currently shown in the default Computers container, not the custom Workstations OU. This is an inventory finding, not automatically an error. The intended placement should be decided and documented before moving the computer object.

## 7. Group Policy Objects

The supplied GPO inventory lists:

- Default Domain Policy — AllSettingsEnabled
- Default Domain Controllers Policy — AllSettingsEnabled

No custom GPO appears in the supplied output. This inventory does not show GPO link locations, individual settings, security filtering, WMI filtering or resultant policy on MT-WS01. Those require separate inspection and testing.

## 8. File shares

The following departmental shares are visible:

| Share | Local path |
|---|---|
| IT | C:\CompanyData\IT |
| Finance | C:\CompanyData\Finance |
| HR | C:\CompanyData\HR |
| Admin | C:\CompanyData\Admin |

Standard administrative shares and the NETLOGON/SYSVOL shares are also listed.

### Share observations and limitations

- No Management share appears in the supplied share inventory.
- The output lists share names and paths only. It does not show share-level permissions, NTFS ACLs, inheritance, ownership or effective access.
- Do not assume departmental isolation is working until both share permissions and NTFS permissions are inspected and tested using representative user accounts.

## 9. Gap and anomaly register

| ID | Finding | Priority | Recommended next action |
|---|---|---|---|
| AD-01 | Management OU absent from visible department OUs | Medium | Confirm department requirement, then add Management OU under Departments |
| AD-02 | No Management employee accounts listed | Medium | Define synthetic employee identities and naming convention before creation |
| AD-03 | No GG_Management_Users group listed | Medium | Create a global security group after confirming target design |
| AD-04 | No Management file share listed | Medium | Create only after directory and access design is approved |
| AD-05 | Blank/whitespace-looking OU row | High investigation priority | Inspect exact OU name, DN, parent and child objects; do not delete yet |
| AD-06 | MT-WS01 is in default Computers container | Low / design decision | Decide whether to move it into the existing Workstations OU |
| AD-07 | Only default GPOs listed | Medium | Design and test custom workstation/security policies |
| AD-08 | Share and NTFS ACLs not included | High validation priority | Audit share permissions and filesystem ACLs before claiming access control |
| AD-09 | DNS health evidence not included in this inventory excerpt | Medium | Capture DNS zone, SRV lookup and dcdiag test output |

## 10. Recommended implementation sequence

1. Inspect the blank/whitespace-looking OU and confirm its exact DN and contents.
2. Confirm the intended departmental OU design and whether Management is an in-scope department.
3. If confirmed, create Management under the existing Departments OU; do not rename Admin.
4. Define two synthetic Management employee accounts, following the existing naming convention, after checking for duplicate SamAccountNames.
5. Create GG_Management_Users as a global security group and add only the intended Management users.
6. Decide whether MT-WS01 should be moved into the existing Workstations OU.
7. Audit share-level permissions and NTFS ACLs on IT, Finance, HR and Admin shares.
8. Design the Management share and its permissions only after the access model is agreed.
9. Design custom GPOs and verify application on the workstation.
10. Capture before-and-after evidence and update the status register.

## 11. Additional read-only PowerShell checks

Run these checks on MT-DC01 before making changes.

### Inspect the suspicious OU

```powershell
Get-ADOrganizationalUnit -Filter * -Properties Name, DistinguishedName |
    Format-List Name, DistinguishedName
```

Copy the exact DN of the suspicious OU, then inspect its direct child objects:

```powershell
Get-ADObject -SearchBase "<PASTE-EXACT-OU-DN-HERE>" -SearchScope OneLevel -Filter * |
    Select-Object Name, ObjectClass, DistinguishedName
```

### Confirm department OUs and accounts

```powershell
Get-ADOrganizationalUnit -SearchBase "OU=Departments,OU=Mothibedi Technologies,DC=ad,DC=mothibedi,DC=test" -SearchScope OneLevel -Filter * |
    Select-Object Name, DistinguishedName

Get-ADUser -SearchBase "OU=Departments,OU=Mothibedi Technologies,DC=ad,DC=mothibedi,DC=test" -SearchScope Subtree -Filter * -Properties Enabled |
    Select-Object Name, SamAccountName, Enabled, DistinguishedName
```

### Inspect share permissions and NTFS ACLs

```powershell
Get-SmbShare -Name IT,Finance,HR,Admin |
    Select-Object Name, Path

Get-SmbShareAccess -Name IT
Get-SmbShareAccess -Name Finance
Get-SmbShareAccess -Name HR
Get-SmbShareAccess -Name Admin

Get-Acl "C:\CompanyData\IT" | Format-List
Get-Acl "C:\CompanyData\Finance" | Format-List
Get-Acl "C:\CompanyData\HR" | Format-List
Get-Acl "C:\CompanyData\Admin" | Format-List
```

### Inspect workstation OU and GPO links

```powershell
Get-ADComputer MT-WS01 -Properties DistinguishedName |
    Select-Object Name, DistinguishedName

Get-GPO -All | Select-Object DisplayName, GpoStatus
Get-GPInheritance -Target "OU=Workstations,OU=Mothibedi Technologies,DC=ad,DC=mothibedi,DC=test"
```

These are inspection commands. They do not create or modify users, groups, OUs, GPOs, shares or permissions.

## 12. Audit conclusion

The supplied audit demonstrates a working AD domain structure with four populated departments, eight enabled departmental employee accounts, four departmental global security groups, two computer objects and four departmental shares.

The next logical improvement is to complete the Management department consistently across the directory and file services, but only after inspecting the anomalous OU and confirming the design. Before claiming secure departmental file access, collect and test both share-level and NTFS permissions. Custom GPO implementation and DNS health evidence also remain outstanding.

This report describes only what was present in the supplied audit output. It does not claim that the recommended changes have already been performed.

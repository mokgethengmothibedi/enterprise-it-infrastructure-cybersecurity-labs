# Project Status and Evidence Register

**Last updated:** 2026-11-21

Status definitions: **Complete** means user-confirmed implementation; **In progress** means partially implemented or awaiting validation; **Pending** means not yet implemented; **To verify** means inspect the live state before making changes.

## Lab platform

| Item | Status | Recorded facts |
|---|---|---|
| Ubuntu desktop | Complete | User reported Ubuntu installed; 16 GB RAM |
| GNS3 | Complete | Installed and working |
| QEMU/KVM | Complete | Installed and working |
| GNS3/libvirt NAT | Complete | Internet access from lab confirmed |
| Lab subnet | Complete | 192.168.122.0/24 |
| Default gateway | Complete | 192.168.122.1 |

## Project 01 — Windows infrastructure

| Item | Status | Recorded facts / next action |
|---|---|---|
| Windows Server | Complete | Server VM named MT-DC01 |
| AD DS promotion | Complete | Domain controller for ad.mothibedi.test |
| DC address | Complete | 192.168.122.10 |
| DNS role | In progress | Installed; record forward/reverse lookups and DC locator tests |
| Existing OU structure | To verify | User confirmed OUs/departments visible in ADUC; exact tree not yet audited |
| Management OU | Pending / to verify | User reported it was omitted from earlier OU creation; inspect before adding |
| Department accounts | To verify | Exact names, enabled state and OU placement not confirmed |
| Security groups | To verify | Exact group names and memberships not confirmed |
| Windows 11 workstation | Complete | MT-WS01 installed and renamed |
| Domain join | Complete | User confirmed MT-WS01 joined ad.mothibedi.test |
| Domain sign-in / discovery / secure channel | User-reported complete | User reported checks completed without errors; raw output still needed |
| Custom GPOs | Pending | No custom policy evidence recorded |
| File shares and NTFS permissions | Pending | No actual share/ACL evidence recorded |
| PowerShell administration scripts | Pending | Build after directory audit |
| Backup and recovery | Pending | Not yet evidenced |
| Scenario reports | Pending | Use the scenario template |

## Projects 02 and 03

| Project | Status | Next milestone |
|---|---|---|
| Project 02 — Network engineering & security | Planned | Requirements, topology and addressing design |
| Project 03 — Security operations & monitoring | Planned | Monitoring architecture and tool selection |

## Next evidence to collect from MT-DC01

Run these read-only PowerShell commands in an elevated PowerShell session and save the output for review:

~~~powershell
Get-ADDomain | Select-Object DNSRoot, NetBIOSName, DomainMode
Get-ADForest | Select-Object RootDomain, ForestMode
Get-ADOrganizationalUnit -Filter * -Properties DistinguishedName |
    Select-Object Name, DistinguishedName |
    Sort-Object DistinguishedName
Get-ADUser -Filter * -Properties Enabled, DistinguishedName |
    Select-Object SamAccountName, Enabled, DistinguishedName |
    Sort-Object DistinguishedName, SamAccountName
Get-ADGroup -Filter * -Properties GroupScope, GroupCategory |
    Select-Object Name, GroupScope, GroupCategory, DistinguishedName |
    Sort-Object Name
Get-DnsServerZone
dcdiag /test:dns
~~~

These commands inspect the current state; they do not create or modify AD objects. Review output for sensitive information before publishing.

## Verification rule

Do not assume a proposed OU, user, group, share, GPO or test exists because it appeared in an earlier plan or example. Collect the live AD inventory and compare it with the target design before changing the directory. Avoid duplicate accounts and groups.

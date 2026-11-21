# Project Status and Evidence Register

**Last updated:** 2026-11-21  
**Latest evidence:** [Active Directory PowerShell Audit Report](project-01-windows-infrastructure/04-active-directory/AD-AUDIT-REPORT.md)

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
| Windows Server | Complete | MT-DC01 installed |
| AD DS promotion | Complete | Domain ad.mothibedi.test; NetBIOS MOTHIBEDI |
| DC address | Complete | 192.168.122.10 |
| Existing department OUs | Complete | IT, Finance, HR and Admin under Departments |
| Management OU | Pending | Not present in supplied audit; add only after confirming target design |
| Employee accounts | Complete for four existing departments | Eight enabled users; two each in IT, Finance, HR and Admin |
| Management employee accounts | Pending | None listed in supplied audit |
| Department security groups | Complete for four existing departments | GG_IT_Users, GG_Finance_Users, GG_HR_Users, GG_Admin_Users; all global security groups |
| Management security group | Pending | No GG_Management_Users listed |
| Suspicious blank/whitespace OU | To verify | Audit shows an anomalous OU row; inspect exact DN and contents before any cleanup |
| Workstations OU | Exists | Under Mothibedi Technologies |
| MT-WS01 placement | To verify / design decision | Audit lists it in default CN=Computers container |
| DNS | In progress | Role installed; collect DNS zone, SRV lookup and dcdiag evidence |
| Windows 11 workstation | Complete | MT-WS01 installed, renamed and domain-joined per user confirmation |
| Custom GPOs | Pending | Audit lists only Default Domain Policy and Default Domain Controllers Policy |
| Department shares | Complete as share objects | IT, Finance, HR and Admin shares exist under C:\CompanyData |
| Management share | Pending | Not listed in supplied audit |
| Share and NTFS permissions | To verify | Audit contains share names/paths, not ACLs or effective-access tests |
| PowerShell automation | Pending | Plan after directory structure and permissions are validated |
| Backup and recovery | Pending | Not yet evidenced |
| Scenario reports | In progress | Audit report committed; operational scenarios still to be performed |

## Projects 02 and 03

| Project | Status | Next milestone |
|---|---|---|
| Project 02 — Network engineering & security | Planned | Requirements, topology and addressing design |
| Project 03 — Security operations & monitoring | Planned | Monitoring architecture and tool selection |

## Next actions for Project 01

1. Inspect the blank/whitespace-looking OU and its children. Do not delete or rename it until understood.
2. Confirm and implement the Management OU, employee accounts and global security group.
3. Decide whether MT-WS01 should be moved from the default Computers container into the existing Workstations OU.
4. Audit share permissions and NTFS ACLs for the four existing departmental shares.
5. Implement Management file share and access rules after agreeing the access model.
6. Design custom GPOs and verify their application on MT-WS01.
7. Capture DNS health tests and complete scenario-based validation.

The audit report is a snapshot of supplied output. It does not establish that share permissions, NTFS ACLs, GPO links or DNS health tests are correct.

# Project 01 — Enterprise Windows Infrastructure

**Status: In progress**

## Business scenario

Mothibedi Technologies is a fictional organisation with IT, Finance, HR, Admin and Management departments. It needs centralised identity administration, managed Windows endpoints, reliable name resolution and controlled access to departmental resources.

## Objective

Build a small Windows domain and demonstrate practical service-desk and systems-administration tasks: account lifecycle management, DNS troubleshooting, endpoint domain integration, policy management, file permissions, automation and recovery.

## Environment

- Host: Ubuntu desktop, 16 GB RAM.
- Virtualisation/networking: GNS3 with QEMU/KVM and libvirt NAT.
- Lab subnet: 192.168.122.0/24; gateway: 192.168.122.1.
- Domain controller: MT-DC01, 192.168.122.10.
- Active Directory domain: ad.mothibedi.test (NetBIOS: MOTHIBEDI).
- Workstation: MT-WS01, Windows 11, domain-joined per user confirmation.

## Current Active Directory audit findings

The supplied PowerShell audit confirms four populated departments: IT, Finance, HR and Admin. Eight enabled employee accounts are listed, two in each department. Four matching global security groups exist: GG_IT_Users, GG_Finance_Users, GG_HR_Users and GG_Admin_Users.

Management is not present in the supplied OU, user, group or share inventories. An anomalous blank/whitespace-looking OU row also appears and must be inspected before any cleanup.

The audit lists MT-WS01 in the default Computers container rather than the custom Workstations OU. Only the two default domain GPOs are listed. Four departmental shares exist (IT, Finance, HR and Admin), but their share-level and NTFS permissions have not yet been audited.

Read the complete [Active Directory PowerShell Audit Report](04-active-directory/AD-AUDIT-REPORT.md) before making directory changes.

## Workstreams

1. Requirements, architecture and IP addressing.
2. Windows Server foundation and domain services.
3. AD organisational units, user lifecycle and security groups.
4. Windows 11 domain workstation.
5. Group Policy and endpoint configuration.
6. Department file services and least-privilege permissions.
7. PowerShell automation.
8. Backup and recovery.
9. Scenario-based troubleshooting and validation.

## Scenario catalogue

| ID | Scenario | Competency |
|---|---|---|
| WIN-01 | New employee onboarding | AD account creation, OU placement and group assignment |
| WIN-02 | Department transfer | Access review and group membership changes |
| WIN-03 | Employee offboarding | Account disablement and access revocation |
| WIN-04 | Password reset | Identity support and authentication validation |
| WIN-05 | Account lockout | Event investigation and root-cause analysis |
| WIN-06 | Department share access denied | Share permissions, NTFS ACLs and effective access |
| WIN-07 | Workstation cannot locate DC | DNS, network and domain discovery troubleshooting |
| WIN-08 | Group Policy not applying | GPO scope, inheritance, filtering and client diagnostics |
| WIN-09 | Backup and recovery | Resilience and restore validation |

## Evidence requirements

For each workstream include a design note, implementation steps, sanitised screenshots, command output, expected-versus-actual results, troubleshooting notes and lessons learned. Use the [scenario report template](../templates/SCENARIO-REPORT-TEMPLATE.md).

## Immediate next step

Inspect the anomalous OU and audit existing share/NTFS permissions. Then complete the Management department consistently across OUs, employee accounts, security groups and file services. Do not create duplicate objects or delete unknown directory objects.

# Project 01 — Enterprise Windows Infrastructure

**Status: In progress**

## Business scenario

Mothibedi Technologies is a fictional organisation with IT, Finance, HR, Admin and Management departments. It needs centralised identity administration, managed Windows endpoints, reliable name resolution and controlled access to departmental resources.

## Objective

Build a small Windows domain and demonstrate practical service-desk and systems-administration tasks: account lifecycle management, DNS troubleshooting, endpoint domain integration, policy management, file permissions, automation and recovery.

## Environment recorded so far

- Host: Ubuntu desktop, 16 GB RAM.
- Virtualisation/networking: GNS3 with QEMU/KVM and libvirt NAT.
- Lab subnet: 192.168.122.0/24; gateway: 192.168.122.1.
- Domain controller: MT-DC01, 192.168.122.10.
- Active Directory domain: ad.mothibedi.test.
- Workstation: MT-WS01, Windows 11, domain-joined per user confirmation.

The exact OU, user and group inventory is intentionally not listed until audited on MT-DC01.

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

Collect the read-only AD inventory from MT-DC01. Confirm the existing OU tree, accounts, groups and memberships before adding the missing Management structure or creating employee accounts.

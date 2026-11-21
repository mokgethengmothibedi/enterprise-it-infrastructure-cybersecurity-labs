# Enterprise IT Infrastructure & Cybersecurity Labs

**Portfolio owner:** Mokgetheng Mothibedi  
**Status:** Project 01 in progress; Projects 02 and 03 planned  
**Tools:** GNS3, QEMU/KVM, Ubuntu, Windows Server, Windows 11, PowerShell and free/open-source tools.

## Overview

This repository documents a practical, scenario-driven portfolio covering enterprise IT infrastructure, systems administration, networking and cybersecurity operations. The aim is to demonstrate requirements analysis, implementation, validation, troubleshooting and clear technical documentation.

### Three connected projects

1. **Enterprise Windows Infrastructure** — Windows Server, Active Directory, DNS, domain workstations, Group Policy, file services and administration.
2. **Enterprise Network Engineering & Security** — network segmentation, VLANs, routing, firewall policy, VPN concepts and packet analysis.
3. **IT Operations & Cybersecurity Monitoring** — centralised logging, endpoint monitoring, alert investigation and incident response.

## Current implementation snapshot

The lab runs on an Ubuntu desktop with 16 GB RAM using GNS3 and QEMU/KVM. The current virtual network uses libvirt NAT.

| Component | Recorded state |
|---|---|
| Ubuntu, GNS3 and QEMU/KVM | Set up and working |
| Lab network / internet access | Working; lab uses 192.168.122.0/24 |
| Windows Server domain controller | Installed and promoted as MT-DC01 |
| AD domain | ad.mothibedi.test |
| Domain controller address | 192.168.122.10 |
| DNS | Installed; detailed validation evidence still to be recorded |
| Windows 11 workstation | MT-WS01 installed and domain-joined, per user confirmation |
| Exact OU, user and group inventory | Awaiting live audit |
| Custom GPOs, file shares, ACLs, automation and recovery tests | Pending |

See [Project Status](PROJECT-STATUS.md) and [Roadmap](ROADMAP.md).

## Documentation standard

Every practical scenario should record its business context, objective, prerequisites, design, implementation steps, commands, expected result, actual result, validation evidence, troubleshooting, security implications and lessons learned. Expected output must never be presented as observed output.

## Repository map

- [Roadmap](ROADMAP.md)
- [Project status](PROJECT-STATUS.md)
- [Project 01 — Windows infrastructure](project-01-windows-infrastructure/README.md)
- [Project 02 — Network engineering and security](project-02-network-security/README.md)
- [Project 03 — Security operations and monitoring](project-03-security-operations/README.md)
- [Scenario report template](templates/SCENARIO-REPORT-TEMPLATE.md)
- [Skills matrix](portfolio/SKILLS-MATRIX.md)

## Safety and integrity

This is a learning lab, not a production environment. Use synthetic users and test data. Never commit passwords, private keys, recovery keys, tokens or real personal information. Review and redact screenshots before publishing. Test only systems and networks you own or are authorised to assess.

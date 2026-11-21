# Portfolio Roadmap

## Business scenario

Mothibedi Technologies is a fictional organisation with IT, Finance, HR, Admin and Management departments. It requires managed identities, reliable endpoints, controlled access to information, secure connectivity and visibility into infrastructure events.

## Project 01 — Enterprise Windows Infrastructure

**Objective:** Build and administer a small enterprise Windows domain.

| Phase | Implementation work | Desired evidence / acceptance criteria |
|---|---|---|
| 1. Requirements and design | Define business needs, roles, trust boundaries, hostnames and IP plan | Requirements, topology and addressing table |
| 2. Virtual platform | GNS3, QEMU/KVM, virtual network and VM resources | VM inventory, topology and connectivity tests |
| 3. Server foundation | Install Windows Server, set hostname and static network | Server configuration and reachability tests |
| 4. Identity and DNS | AD DS promotion, domain health and DNS records | Domain details, DNS lookups and DC locator output |
| 5. Directory structure | Audit and implement OUs, departmental users, groups and memberships | OU tree and sanitised user/group inventory |
| 6. Endpoint deployment | Configure Windows client DNS, join domain and test sign-in | Domain discovery, secure-channel and logon tests |
| 7. Group Policy | Create and link GPOs; test scope and resultant policy | GPMC evidence, gpresult output and policy test |
| 8. File services | Department shares and share + NTFS permissions | Access matrix and allowed/denied access tests |
| 9. Automation | Safe PowerShell scripts for repeatable administration | Scripts, usage notes and validation output |
| 10. Resilience | Back up selected configuration/data and test recovery | Backup plan and recorded restore result |
| 11. Operational scenarios | Execute incidents and service requests | Completed scenario reports and evidence |
| 12. Final review | Review security and completeness | Final assessment and skills matrix |

### Project 01 scenario acceptance tests

- Onboard a synthetic employee and assign correct department access.
- Transfer an employee and remove access that is no longer required.
- Offboard an employee and verify sign-in and access are revoked.
- Reset a password and validate sign-in behaviour.
- Investigate a simulated account lockout using event evidence.
- Verify authorised share access and denial for unauthorised users.
- Diagnose a client DNS or domain-controller discovery fault.
- Diagnose a Group Policy application problem.
- Demonstrate a documented backup and recovery test.

## Project 02 — Enterprise Network Engineering & Security

**Objective:** Design and validate a segmented two-site network for a fictional Johannesburg HQ and Cape Town branch.

| Phase | Implementation work | Desired evidence |
|---|---|---|
| 1. Requirements | Identify departments, services and connectivity needs | Requirements and traffic-flow matrix |
| 2. Logical design | Design HQ/branch topology and subnets | Network diagram and subnetting table |
| 3. Segmentation | Departmental VLANs and access/trunk links | Switch configuration and VLAN verification |
| 4. Routing | Inter-VLAN and site routing | Routing tables and end-to-end tests |
| 5. Security controls | Firewall/ACL policy using least privilege | Rule matrix and allowed/blocked tests |
| 6. Remote connectivity | Lab-appropriate site-to-site VPN | Tunnel status and protected traffic test |
| 7. Traffic analysis | Wireshark capture and interpretation | Sanitised PCAPs and findings |
| 8. Incident scenarios | Investigate misconfiguration and blocked traffic | Troubleshooting reports and corrective actions |

Scenario outcomes include a department unable to reach an approved service, blocked unauthorised inter-VLAN access, branch connectivity loss, and packet analysis to isolate DNS, routing or transport faults.

## Project 03 — IT Operations & Cybersecurity Monitoring

**Objective:** Centralise infrastructure visibility and practise alert triage and incident response.

| Phase | Implementation work | Desired evidence |
|---|---|---|
| 1. Monitoring design | Define assets, log sources and critical events | Monitoring architecture and use cases |
| 2. Linux foundation | Deploy and harden a Linux monitoring host | Host configuration and service status |
| 3. SIEM | Deploy Wazuh and connect supported endpoints | Agent status, collected events and dashboard |
| 4. Infrastructure monitoring | Deploy Zabbix or equivalent free tool | Availability and resource dashboards |
| 5. Detection | Configure/tune detection rules | Rule rationale, test event and alert |
| 6. Incident response | Triage simulated authentication and endpoint events | Timeline, severity, investigation and response |
| 7. Reporting | Produce operational/security summaries | Incident report and monitoring review |

Scenario outcomes include repeated failed logons, unexpected account activity, endpoint outage, high resource utilisation and a benign suspicious-event simulation. Any simulation must be safe and confined to the lab.

## Completion standard

A phase is complete only when its design and implementation are documented, commands are explained, expected and actual results are separated, tests are repeatable, evidence is sanitised, and limitations and lessons learned are stated honestly.

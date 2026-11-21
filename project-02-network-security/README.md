# Project 02 — Enterprise Network Engineering & Security

**Status: Planned**

## Business scenario

A fictional organisation operates a Johannesburg headquarters and a Cape Town branch. Departmental systems require controlled connectivity to shared services while remaining isolated from unrelated networks.

## Objective

Design, implement and validate a segmented enterprise network using free lab tools. Demonstrate addressing, VLANs, routing, firewall policy, VPN connectivity and packet-level troubleshooting.

## Planned workstreams

1. Requirements, assets and traffic-flow matrix.
2. Logical topology and IP subnetting plan.
3. Departmental VLANs and switch port configuration.
4. Inter-VLAN routing and route validation.
5. Firewall/ACL policy using least privilege.
6. Site-to-site VPN in a supported lab topology.
7. Wireshark packet capture and protocol analysis.
8. Fault-injection and troubleshooting scenarios.

## Scenario catalogue

- A user in one VLAN cannot reach an approved business service.
- A user attempts to reach a restricted departmental subnet and is blocked.
- The branch loses connectivity to headquarters.
- DNS resolution works but the application connection fails.
- Packet capture is used to distinguish name-resolution, routing and transport-layer faults.

## Desired evidence

Topology diagram, VLAN and subnet tables, device configurations, routing tables, firewall rule matrix, VPN status, sanitised packet captures, connectivity tests and scenario reports.

No implementation is claimed until configurations and test results are captured in this repository.

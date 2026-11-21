# Project 03 — IT Operations & Cybersecurity Monitoring

**Status: Planned**

## Business scenario

The organisation needs visibility into endpoint health, authentication activity and infrastructure availability. IT staff must detect, investigate, document and respond to operational and security events.

## Objective

Build a small monitoring and security-operations environment using free tools. Centralise selected logs, monitor infrastructure health, generate controlled test events and practise incident triage.

## Planned components

- Linux monitoring host.
- Wazuh for endpoint security monitoring and log analysis.
- Wazuh agents on supported Windows/Linux endpoints.
- Zabbix or an equivalent free tool for infrastructure availability and resource monitoring.
- Documented detection use cases and incident response workflow.

Final tool versions and deployment topology will be recorded when implementation begins.

## Scenario catalogue

- Repeated failed authentication attempts.
- Unexpected account or privilege activity.
- A monitored endpoint becomes unavailable.
- CPU, memory or disk utilisation exceeds a defined threshold.
- A suspicious but benign test event is generated and investigated.
- An alert is triaged, prioritised, documented and closed with lessons learned.

## Desired evidence

Monitoring architecture, agent status, sample event records, alert screenshots, detection-rule rationale, investigation timeline, incident report and remediation recommendations.

All simulations must be benign and confined to systems owned or authorised by the lab operator.

# Wazuh Blue Team Lab

![Wazuh](https://img.shields.io/badge/Wazuh-SIEM-blue)
![MITRE ATT&CK](https://img.shields.io/badge/MITRE-ATT%26CK-red)
![Sysmon](https://img.shields.io/badge/Sysmon-Endpoint%20Monitoring-green)
![Windows](https://img.shields.io/badge/Windows-10-blue)
![Ubuntu](https://img.shields.io/badge/Ubuntu-Server-orange)

## Overview

This project documents the deployment of a Wazuh-based Security Monitoring Lab used for Blue Team operations, threat hunting, and MITRE ATT&CK detection validation.

The environment includes:

- Wazuh Manager running on Ubuntu Server
- Windows 10 endpoint monitored with Sysmon
- Atomic Red Team simulations
- MITRE ATT&CK mapping
- Custom detection rules
- Event investigation and threat hunting workflows

---

## Lab Architecture

| Component | Description |
|------------|------------|
| Wazuh Manager | Centralized SIEM platform |
| Ubuntu Server | Hosts Wazuh services |
| Windows 10 Endpoint | Target monitored host |
| Sysmon | Advanced endpoint telemetry |
| Atomic Red Team | Attack simulation framework |

---

## Active Agents

The environment consists of a Windows endpoint and a Linux-based Wazuh server.

![Active Agents](screenshots/wazuh-active-agents.png)

---

## MITRE ATT&CK Mapping

Atomic Red Team simulations were successfully detected and mapped to MITRE ATT&CK techniques through Wazuh correlation rules.

![MITRE ATT&CK Detection](screenshots/wazuh-mitre-t1053.png)

---

## Custom Detection Rules

Custom detection rules were developed and validated against Atomic Red Team tests.

### Rule 115001 - Scheduled Task Detection

**MITRE ATT&CK:** T1053 - Scheduled Task

**Description**

> A Newly Scheduled Task has been Detected on Windows10

**Detection Example**

![Scheduled Task Detection](screenshots/scheduled-task-detection.png)

---

### Rule 115003 - Security Software Discovery

**MITRE ATT&CK:** T1518 - Security Software Discovery

**Description**

> Security Software Discovery Attempt has been Detected on Windows10

**Detection Example**

![Security Software Discovery](screenshots/security-software-discovery-t1518.png)

---

## Skills Demonstrated

- Security Monitoring
- Threat Hunting
- SIEM Administration
- Endpoint Monitoring
- Sysmon Deployment
- MITRE ATT&CK Mapping
- Detection Engineering
- Wazuh Administration
- Atomic Red Team Testing
- Log Analysis

---

## Technologies Used

- Wazuh
- Sysmon
- Ubuntu Server
- Windows 10
- Docker
- Portainer
- Atomic Red Team
- MITRE ATT&CK

---

## Future Improvements

- Linux Threat Hunting
- YARA Integration
- VirusTotal Integration
- Grafana Dashboards
- Additional Detection Rules
- Multi-endpoint Monitoring

---

## Author

**Angelo Morozini**

Cybersecurity Student focused on Blue Team Operations, Threat Hunting, Detection Engineering and Security Monitoring.

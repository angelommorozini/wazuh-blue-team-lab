# Wazuh Blue Team Lab

![Wazuh](https://img.shields.io/badge/Wazuh-v4.14.5-blue)
![MITRE ATT&CK](https://img.shields.io/badge/MITRE-ATT%26CK-red)
![Sysmon](https://img.shields.io/badge/Sysmon-Endpoint%20Monitoring-green)
![Windows](https://img.shields.io/badge/Windows-10-blue)
![Ubuntu](https://img.shields.io/badge/Ubuntu-Server-orange)

> A hands-on Security Monitoring Lab simulating real-world Blue Team operations, with custom Wazuh detection rules validated against MITRE ATT&CK techniques using Atomic Red Team.

---

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
|-----------|-------------|
| Wazuh Manager | Centralized SIEM platform (v4.14.5) |
| Ubuntu Server | Hosts Wazuh services |
| Windows 10 Endpoint | Target monitored host |
| Sysmon | Advanced endpoint telemetry |
| Atomic Red Team | Attack simulation framework |
| Docker + Portainer | Container management |

---

## Setup & Requirements

| Item | Details |
|------|---------|
| Wazuh Version | v4.14.5 |
| Host OS (Manager) | Ubuntu Server |
| Host OS (Endpoint) | Windows 10 |
| RAM | 16GB |

### Quick Start

1. Deploy Wazuh Manager on Ubuntu following the [official docs](https://documentation.wazuh.com)
2. Install and configure Sysmon on the Windows endpoint
3. Enroll the Windows agent on Wazuh Manager
4. Import the custom detection rules (see section below)
5. Run Atomic Red Team tests to validate detections

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

---

### Rule 115001 — Scheduled Task Detection

**MITRE ATT&CK:** T1053 - Scheduled Task  
**Description:** A Newly Scheduled Task has been Detected on the monitored endpoint.

```xml
<group name="windows,sysmon,custom_detection,">
  <rule id="115001" level="10">
    <if_sid>61613</if_sid>
    <field name="win.eventdata.ruleName">technique_id=T1053</field>
    <description>A Newly Scheduled Task has been Detected on $(agent.name)</description>
    <mitre>
      <id>T1053</id>
    </mitre>
  </rule>
</group>
```

**Detection Example**

![Scheduled Task Detection](screenshots/scheduled-task-detection.png)

---

### Rule 115003 — Security Software Discovery

**MITRE ATT&CK:** T1518 - Security Software Discovery  
**Description:** Security Software Discovery Attempt detected via `fltmc.exe` execution on the monitored endpoint.

```xml
<rule id="115003" level="10">
  <if_sid>61603</if_sid>
  <field name="win.eventdata.image">(?i)fltmc\.exe</field>
  <description>Security Software Discovery Attempt has been Detected on $(agent.name)</description>
  <mitre>
    <id>T1518</id>
  </mitre>
</rule>
```

**Detection Example**

![Security Software Discovery](screenshots/security-software-discovery-t1518.png)

---

## Skills Demonstrated

- Detection Engineering
- SIEM Administration
- Threat Hunting
- Endpoint Monitoring
- Sysmon Deployment
- MITRE ATT&CK Mapping
- Atomic Red Team Testing
- Log Analysis
- Wazuh Administration
- Security Monitoring

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

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Angelo%20Morozini-blue?logo=linkedin)](https://www.linkedin.com/in/angelo-morozini)

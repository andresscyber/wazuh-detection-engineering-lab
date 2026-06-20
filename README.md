# Wazuh Detection Engineering Lab

## Overview

This project demonstrates how to build a Detection Engineering lab using Wazuh, Sysmon, and Windows event telemetry.

The lab collects Windows endpoint logs, forwards them to a centralized Wazuh manager, and uses custom detection rules to identify potentially suspicious activity.

Custom detections were developed and mapped to MITRE ATT&CK techniques to simulate a real-world Security Operations Center (SOC) workflow.

---

## Objectives

- Deploy a Wazuh SIEM environment
- Install and configure Sysmon telemetry
- Collect Windows Security and Sysmon logs
- Create custom Wazuh detection rules
- Generate simulated attack activity
- Map detections to MITRE ATT&CK
- Perform threat hunting and alert validation

---

## Technologies Used

- Wazuh
- Sysmon
- Windows 10
- Ubuntu Server
- PowerShell
- Windows Event Logs
- MITRE ATT&CK Framework

---

## Architecture

![Architecture](architecture/lab-architecture.png)

### Data Flow

Windows Endpoint → Sysmon → Wazuh Agent → Wazuh Manager → Custom Detection Rules → Wazuh Dashboard

---

# Environment Validation

Verified communication between the Windows endpoint and Wazuh manager.

![Environment Validation](screenshots/01-environment-validation/02-windows-agent-active.png)

---

# Sysmon Telemetry Collection

Validated Sysmon process creation telemetry and confirmed events were successfully ingested into Wazuh.

### Sysmon Event ID 1

![Sysmon Event](screenshots/02-sysmon-telemetry/01-sysmon-event-id-1-process-creation.png)

### Events Visible in Wazuh

![Wazuh Events](screenshots/02-sysmon-telemetry/02-events-visible-in-wazuh.png)

---

# Custom Detection Rule Development

Created custom Wazuh detection rules to identify suspicious activity.

### PowerShell Execution Detection

Rule ID: 100100

MITRE ATT&CK: T1059.001 – PowerShell

Detects execution of SecEdit through PowerShell.

---

# Detection 1: PowerShell Execution

Simulated PowerShell execution activity and validated custom alert generation.

![PowerShell Detection](screenshots/04-detection-powershell/04-custom-powershell-alert-triggered.png)

---

# Detection 2: User Account Creation

Created a new local user account and generated a custom Wazuh alert.

Rule ID: 100101

MITRE ATT&CK: T1136 – Create Account

![User Account Detection](screenshots/05-detection-new-user/05-custom-account-alert-triggered.png)

---

# Detection 3: Privilege Escalation

Added a user account to the local Administrators group and generated a custom alert.

Rule ID: 100102

MITRE ATT&CK: T1484 – Domain Policy Modification

![Privilege Escalation Detection](screenshots/06-detection-admin-group/03-custom-admin-group-alert.png)

---

# Scheduled Task Activity

Created a scheduled task to simulate persistence-related activity.

![Scheduled Task](screenshots/07-detection-scheduled-task/01-scheduled-task-created.png)

---

# Network Telemetry Analysis

Reviewed Sysmon Event ID 3 network connection telemetry generated from PowerShell activity.

![Network Telemetry](screenshots/08-detection-network-connection/01-network-telemetry-details.png)

---

# MITRE ATT&CK Mapping

### PowerShell Execution

![MITRE PowerShell](screenshots/09-mitre-mapping/01-powershell-mitre.png)

### User Account Creation

![MITRE User Account](screenshots/09-mitre-mapping/02-user-created-mitre.png)

### Privilege Escalation

![MITRE Privilege Escalation](screenshots/09-mitre-mapping/03-admin-group-mitre.png)

---

# Dashboard Validation

Validated all custom detections within the Wazuh dashboard.

### Custom Detection Results

![Custom Detections](screenshots/10-final-dashboard/01-all-custom-detections.png)

### Dashboard Overview

![Dashboard](screenshots/10-final-dashboard/02-dashboard-overview.png)

---

# Custom Rules

Location:

```
rules/custom_rules.xml
```

Implemented custom rules:

| Rule ID | Description | MITRE |
|----------|-------------|--------|
| 100100 | PowerShell Executed SecEdit | T1059.001 |
| 100101 | User Account Created | T1136 |
| 100102 | User Added To Administrators Group | T1484 |

---

# Skills Demonstrated

- Detection Engineering
- Threat Hunting
- SIEM Administration
- Wazuh
- Sysmon
- Windows Event Analysis
- Security Monitoring
- MITRE ATT&CK Mapping
- Custom Rule Development
- PowerShell Analysis

---

# Resume Highlights

- Built a Wazuh-based detection engineering lab integrating Sysmon telemetry from Windows endpoints for centralized security monitoring.

- Developed custom Wazuh detection rules identifying PowerShell execution, account creation, and administrator group membership changes mapped to MITRE ATT&CK techniques.

- Performed threat hunting and alert analysis using Windows Security Events, Sysmon logs, and custom SIEM detections to investigate simulated attack activity.
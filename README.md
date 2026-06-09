# Intelligent SOC Automation & Threat Hunting Platform

## Overview

The Intelligent SOC Automation & Threat Hunting Platform is an enterprise-grade Security Operations Center (SOC) solution designed to automate security monitoring, threat detection, incident investigation, threat intelligence enrichment, and response workflows.

The platform centralizes logs from multiple sources, performs real-time security analytics using Splunk SIEM, enriches indicators of compromise (IOCs) using threat intelligence feeds, maps detections to the MITRE ATT&CK framework, and automates incident response actions using Python-based SOAR workflows.

This project simulates a modern enterprise SOC environment and demonstrates practical skills in Security Operations, Detection Engineering, Threat Hunting, Incident Response, Threat Intelligence, and Security Automation.



## Key Features

* Centralized log collection and monitoring
* Splunk-based SIEM deployment
* Real-time threat detection and alerting
* Custom SPL detection engineering
* Threat Intelligence enrichment
* MITRE ATT&CK mapping
* Automated IOC analysis
* Security incident triage
* Threat hunting playbooks
* Python-based SOAR automation
* Security dashboards and reporting



## Business Problem

Modern Security Operations Centers receive thousands of alerts daily from various security technologies including firewalls, EDR solutions, operating systems, and network devices.

Security analysts often spend excessive time on:

* Manual alert validation
* Threat intelligence lookups
* Incident prioritization
* IOC enrichment
* Repetitive response tasks

This project aims to reduce analyst workload through automation while improving detection accuracy and incident response efficiency.


## Architecture

```text
Windows Endpoint (Sysmon)
            │
            ▼
Ubuntu Server (Splunk SIEM)
            │
            ▼
Detection Engine (SPL Rules)
            │
            ▼
Threat Intelligence Enrichment
(VirusTotal, AbuseIPDB)
            │
            ▼
MITRE ATT&CK Mapping
            │
            ▼
SOC Dashboard
            │
            ▼
Python SOAR Automation
```



## Technology Stack

### SIEM

* Splunk Enterprise (Free Edition)

### Endpoint Monitoring

* Sysmon
* Windows Event Logs

### Linux Monitoring

* Auditd
* Syslog

### Threat Intelligence

* VirusTotal API
* AbuseIPDB API
* AlienVault OTX

### Detection Engineering

* Splunk SPL
* Sigma Rules

### Threat Hunting

* MITRE ATT&CK Framework
* ATT&CK Navigator

### Automation

* Python
* REST APIs

### Virtualization

* VirtualBox

### Version Control

* Git & GitHub



## Lab Environment

### Splunk Server

| Resource | Configuration       |
| -------- | ------------------- |
| OS       | Ubuntu Server 22.04 |
| RAM      | 4 GB                |
| CPU      | 2 vCPU              |
| Storage  | 50 GB               |

### Endpoint Machine

| Resource | Configuration |
| -------- | ------------- |
| OS       | Windows 10    |
| RAM      | 4 GB          |
| CPU      | 2 vCPU        |
| Storage  | 50 GB         |


## Project Modules

### 1. Log Collection & Monitoring

Collected and normalized logs from:

* Windows Security Events
* Sysmon Logs
* Linux Audit Logs
* Authentication Logs
* Process Creation Events
* Network Connections

### 2. Detection Engineering

Developed custom Splunk detections for:

* Brute Force Attacks
* Account Lockouts
* Suspicious PowerShell Activity
* Privilege Escalation Attempts
* SQL Injection Attempts
* Command Execution Monitoring

### 3. Threat Intelligence Enrichment

Integrated external intelligence sources to enrich:

* IP Addresses
* Domains
* URLs
* File Hashes

Data Sources:

* VirusTotal
* AbuseIPDB
* AlienVault OTX

### 4. MITRE ATT&CK Mapping

Mapped detections to ATT&CK techniques including:

| Detection         | ATT&CK ID |
| ----------------- | --------- |
| Brute Force       | T1110     |
| PowerShell Abuse  | T1059     |
| Credential Access | T1003     |
| Lateral Movement  | T1021     |
| DNS Tunneling     | T1071     |

### 5. Threat Hunting

Implemented hunting queries for:

* DNS Tunneling
* Command & Control Activity
* Lateral Movement
* Credential Abuse
* Suspicious Authentication Activity

### 6. SOAR Automation

Automated workflows for:

* IOC Enrichment
* Threat Scoring
* Alert Prioritization
* Incident Notification
* Automated Response Actions



## Sample Detection Use Cases

### Brute Force Detection

```spl
index=windows EventCode=4625
| stats count by src_ip
| where count > 10
```

### Suspicious PowerShell Activity

```spl
index=sysmon EventCode=1
powershell.exe
```

### Account Lockout Detection

```spl
index=windows EventCode=4740
```



## Threat Hunting Use Cases

### DNS Tunneling

```spl
index=dns
| stats count by query
| where count > 100
```

### Lateral Movement

```spl
index=windows EventCode=4624
Logon_Type=3
```



## Security Metrics

The platform tracks:

### Detection Metrics

* Total Security Alerts
* True Positives
* False Positives
* Detection Coverage

### SOC Metrics

* Mean Time To Detect (MTTD)
* Mean Time To Respond (MTTR)

### Incident Metrics

* Malware Incidents
* Phishing Incidents
* Credential Attacks
* Privilege Escalation Events


## Repository Structure

```text
SOC-Automation-Platform/
│
├── README.md
│
├── Architecture/
│   └── architecture.png
│
├── Detections/
│   ├── brute_force.spl
│   ├── powershell_detection.spl
│   ├── account_lockout.spl
│
├── Threat-Hunting/
│   ├── dns_tunneling.spl
│   ├── lateral_movement.spl
│
├── Automation/
│   ├── virustotal_lookup.py
│   ├── abuseipdb_lookup.py
│
├── Dashboards/
│   └── soc_dashboard.json
│
└── Screenshots/



## Future Enhancements

* Machine Learning Based Alert Prioritization
* User and Entity Behavior Analytics (UEBA)
* CrowdStrike Integration
* Endpoint Isolation Automation
* Malware Sandbox Integration
* Cloud Security Monitoring
* Kubernetes Security Monitoring



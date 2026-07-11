# Splunk-Lab-MTW

> End-to-end deployment of a Splunk Enterprise SIEM environment for centralized Windows event log collection, authentication monitoring, and security analysis.

---

# Project Architecture

![Architecture Diagram](images/architecture.png)

> **Lab Environment**
>
> - Ubuntu Server 24.04 LTS (Splunk Enterprise)
> - Windows Server 2022 Domain Controller
> - Active Directory Domain Services
> - Splunk Universal Forwarder
> - Windows Event Logs (Security, System, Application)

---

## Dashboard Preview

> *(Add your completed Splunk dashboard screenshot here.)*

![Windows Security Dashboard](images/dashboard-overview.png)

The Windows Security Dashboard provides a centralized view of authentication activity across the Active Directory environment. It enables security analysts to quickly identify failed logins, successful logins, account lockouts, authentication trends, Windows security events, and overall log volume within the environment.

---

# Overview

Security teams rely on Security Information and Event Management (SIEM) platforms to collect, centralize, and analyze logs from systems across their environments. Rather than manually reviewing logs on individual servers, analysts use a SIEM to investigate suspicious activity, correlate events, and identify indicators of compromise.

In this project, I deployed **Splunk Enterprise** on an Ubuntu Server virtual machine and configured a Windows Server 2022 Active Directory Domain Controller to forward Windows Event Logs using the Splunk Universal Forwarder.

After configuring log forwarding, I created custom SPL searches to analyze authentication activity and built a Windows Security Dashboard to visualize security events in real time. This project simulates the workflow commonly performed by Tier 1 SOC Analysts during authentication investigations and security monitoring.

---

# Business Problem

Organizations generate thousands of Windows security events every day, including successful logins, failed authentication attempts, account lockouts, service activity, and system events. Without centralized logging, security teams must manually investigate each system individually, increasing investigation time and reducing visibility into potential attacks.

This project demonstrates how Splunk addresses that challenge by centralizing Windows Event Logs into a searchable SIEM platform, allowing analysts to quickly identify suspicious authentication activity, investigate security events, and monitor overall system health through dashboards and SPL searches.

---

## Technologies Used

- Splunk Enterprise
- Splunk Universal Forwarder
- Ubuntu Server 24.04 LTS
- Windows Server 2022
- Active Directory Domain Services
- Windows Event Viewer
- PowerShell
- Linux CLI
- SPL (Splunk Processing Language)
- VMware Workstation

---

## Project Objectives

- Deploy Splunk Enterprise on Ubuntu Linux
- Configure Splunk receiving on port **9997**
- Install the Splunk Universal Forwarder on Windows Server
- Configure Windows Event Log collection using **inputs.conf**
- Forward Security, System, and Application logs into Splunk
- Verify successful log ingestion
- Create custom SPL searches
- Analyze Windows authentication activity
- Build a SOC-style Windows Security Dashboard

---

## Lab Walkthrough

### 1. Installed Splunk Enterprise

Installed Splunk Enterprise on an Ubuntu Server virtual machine and configured the initial administrator account.

**Screenshot**

`images/03-install-complete.png`

---

### 2. Configured Splunk Receiving

Configured Splunk to receive incoming data from Universal Forwarders on TCP port **9997**.

**Screenshot**

`images/33-enable-listening.png`

`images/34-port9997.png`

---

### 3. Installed the Universal Forwarder

Installed the Splunk Universal Forwarder on the Windows Server 2022 Domain Controller and configured both the Deployment Server and Receiving Indexer.

**Screenshots**

`images/21-deployment-server.png`

`images/22-receiving-indexer.png`

---

### 4. Configured Windows Event Collection

Created an **inputs.conf** configuration file to collect:

- Windows Security Logs
- Windows System Logs
- Windows Application Logs

The forwarder was restarted to begin sending telemetry to Splunk.

**Screenshots**

`images/24-inputsconf-location.png`

`images/25-inputsconf.png`

---

### 5. Verified Log Ingestion

Confirmed that Windows Event Logs were successfully being forwarded into the **windows_logs** index.

**Screenshots**

`images/31-forwarding.png`

`images/36-events-arriving.png`

---

### 6. Investigated Windows Authentication Events

Created SPL searches to analyze common Windows security events including:

- Successful Logins (4624)
- Failed Logins (4625)
- Account Lockouts (4740)

Example SPL:

```spl
index=windows_logs sourcetype=WinEventLog:Security EventCode=4625
| stats count by Account_Name
| sort -count
```

---

### 7. Built a Windows Security Dashboard

The dashboard was designed to provide real-time visibility into authentication activity and Windows security events.

Current dashboard panels include:

- Failed Logins
- Successful Logins
- Account Lockouts
- Failed Logins Over Time
- Successful Logins Over Time
- Top Failed Users
- Top Successful Users
- Authentication Success vs Failure
- Logon Types
- Security Event Timeline
- Top Event IDs
- Windows Service Activity
- Recent Failed Logins
- Recent Successful Logins
- Active Directory User Changes
- Group Membership Changes
- Overall Event Volume
- Events by Host
- Events by Sourcetype

---

### 8. Future Improvements

Future enhancements planned for this project include:

- Brute Force Detection Alerts
- Password Spray Detection
- GeoIP Login Visualization
- Windows Defender Event Monitoring
- Sysmon Integration
- PowerShell Logging
- MITRE ATT&CK Mapping
- Additional Detection Rules
- Email Alerting
- Scheduled Reports

---

# What I Learned

Throughout this project I gained hands-on experience with:

- Deploying a SIEM platform from scratch
- Linux system administration
- Installing and configuring Splunk Enterprise
- Configuring Universal Forwarders
- Windows Event Log collection
- Active Directory authentication monitoring
- Writing SPL queries
- Creating Splunk dashboards
- Troubleshooting log forwarding issues
- Investigating Windows Security Event IDs
- Understanding SOC monitoring workflows

---

# Skills Demonstrated

### SIEM

- Splunk Enterprise
- Log Management
- Security Monitoring
- Event Correlation
- Threat Hunting Fundamentals

### Windows

- Active Directory
- Windows Server 2022
- Windows Event Logs
- Authentication Analysis
- Security Event Investigation

### Linux

- Ubuntu Server
- System Administration
- Service Management
- CLI Administration

### Security

- Security Information and Event Management (SIEM)
- Authentication Monitoring
- Account Lockout Investigation
- Windows Security Events
- Security Dashboards

### Networking

- TCP Ports
- Log Forwarding
- Client/Server Communication
- Troubleshooting Connectivity

---

# Key Takeaways

- Successfully deployed Splunk Enterprise on Ubuntu Linux.
- Configured Windows Server log forwarding using the Splunk Universal Forwarder.
- Built a centralized Windows log management solution.
- Collected Security, System, and Application Event Logs into Splunk.
- Investigated authentication activity using SPL searches.
- Built a SOC-style Windows Security Dashboard for monitoring authentication events.
- Developed practical experience with Windows Event IDs commonly investigated by SOC analysts.
- Strengthened troubleshooting skills by resolving connectivity, forwarding, and log ingestion issues throughout deployment.

---

# Portfolio Summary

This project demonstrates my ability to deploy, configure, and operate a Security Information and Event Management (SIEM) platform within a Windows Active Directory environment. Rather than simply installing Splunk, I configured end-to-end log collection using the Splunk Universal Forwarder, centralized Windows Event Logs into a custom index, performed authentication analysis using SPL, and built a security monitoring dashboard that mirrors real-world SOC workflows.

This lab strengthened my experience with Windows Server administration, Active Directory, Linux administration, security monitoring, and SIEM technologies while providing practical exposure to the investigative processes performed by Security Operations Center analysts.

---

# Repository Structure

```
Splunk-Lab-MTW/
│
├── README.md
├── images/
│   ├── dashboard-overview.png
│   ├── architecture.png
│   ├── splunk-install.png
│   ├── forwarding.png
│   ├── inputsconf.png
│   └── dashboard-panels.png
│
├── spl/
│   ├── failed_logins.spl
│   ├── successful_logins.spl
│   ├── lockouts.spl
│   └── dashboard_searches.spl
│
└── docs/
    └── Lab Documentation.pdf
```

---

## Author

**Rico**

Cybersecurity | SOC Analyst | SIEM | Active Directory | Windows Server | Splunk | Linux

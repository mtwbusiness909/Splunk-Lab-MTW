- [**README**](#)

# Splunk-Lab-MTW

## Overview

This project demonstrates the deployment and configuration of **Splunk Enterprise** as a Security Information and Event Management (SIEM) platform for centralized Windows log collection and security monitoring.

A Windows Server Active Directory machine was configured with the **Splunk Universal Forwarder** to securely transmit Security, System, and Application event logs to a dedicated Ubuntu Splunk server. Once ingested, the logs were analyzed using **Splunk Processing Language (SPL)** to identify authentication events, account lockouts, service activity, and other security-related events.

The project concludes with the creation of dashboards and alerts that simulate the responsibilities of a Security Operations Center (SOC) analyst.

---

### Lab Architecture

```
Windows Server
     │
     │ Splunk Universal Forwarder
     │
     ▼
Ubuntu Server (Splunk Enterprise)
     │
     ▼
Indexed Windows Event Logs
     │
     ▼
SPL Searches
     │
     ▼
Dashboards & Alerts
```

---

### Project Screenshots

### Splunk Installation

```
images/1-download-splunk.png
images/2-install-splunk-terminal.png
images/12-start-splunk-service.png
images/16-login-page.png
images/17-splunk-home.png
```

These screenshots demonstrate the installation of Splunk Enterprise on an Ubuntu Server, initial configuration, enabling Splunk services, and accessing the Splunk Web interface.

---

### Universal Forwarder Installation

```
images/18-forwarder-download.png
images/21-deployment-server.png
images/22-receiving-index.png
images/23-forwarder-install-complete.png
```

The Universal Forwarder was installed on the Windows Server and configured to securely send Windows Event Logs to the Splunk indexer.

---

### Configuring inputs.conf

```
images/24-path.png
images/24.5-directory.png
images/25-inputs-conf.png
images/26-inputs-conf-complete.png
```

The **inputs.conf** file was configured to collect:

- Windows Security Logs
- Windows System Logs
- Windows Application Logs

This allowed authentication events, system activity, and application logs to be forwarded into Splunk automatically.

---

### Confirming Data Collection

```
images/30-search-working.png
images/31-windows-events.png
```

After restarting the Splunk Forwarder, Windows Event Logs successfully appeared within the newly created `windows_logs` index.

---

## Business Problem

Organizations generate thousands to millions of security events every day across Active Directory, Windows Servers, workstations, applications, and networking equipment.

Without centralized logging, investigating incidents requires analysts to manually search each individual system, increasing response times and making suspicious activity difficult to identify.

Splunk solves this problem by collecting logs from multiple systems into one searchable platform where security teams can:

- Detect brute force attacks
- Investigate failed authentication attempts
- Monitor user activity
- Search historical events
- Build dashboards for continuous monitoring
- Configure alerts for suspicious behavior

This lab demonstrates how a SIEM improves visibility across an environment while enabling faster incident detection.

---

## What I Learned

Throughout this project I learned how enterprise SIEM platforms ingest, index, search, and visualize security data.

Key concepts included:

- Installing Splunk Enterprise on Ubuntu
- Configuring Linux services
- Deploying the Splunk Universal Forwarder
- Configuring Windows Event Log collection
- Creating a custom Splunk index
- Understanding Windows Security Event IDs
- Writing SPL searches
- Searching authentication events
- Identifying failed logins
- Detecting account lockouts
- Monitoring service activity
- Building dashboards
- Creating scheduled alerts

This project also reinforced how Windows Event IDs can be correlated to identify suspicious authentication behavior commonly investigated by SOC analysts.

---

# Skills Demonstrated

### SIEM

- Splunk Enterprise Deployment
- Splunk Universal Forwarder
- Security Information & Event Management
- Windows Event Log Collection

### Windows Administration

- Active Directory Integration
- Windows Event Viewer
- Windows Security Logs
- Authentication Monitoring

### Linux Administration

- Ubuntu Server
- Linux CLI
- Service Management
- SSH

### Log Analysis

- SPL (Splunk Processing Language)
- Event Searching
- Data Correlation
- Security Monitoring

### Security Monitoring

- Failed Logins (4625)
- Successful Logins (4624)
- Account Lockouts (4740)
- Service Events (7036)
- User Creation Events (4720)

### Detection Engineering

- Dashboards
- Scheduled Searches
- Automated Alerts
- Security Reporting

---

# Dashboard Panels

*(Complete these after generating additional Windows events.)*

## Authentication Overview

- Failed Logins
- Successful Logins
- Failed vs Successful Logins
- Login Activity Over Time

---

## Account Monitoring

- Account Lockouts
- New User Accounts Created
- Password Reset Events
- Group Membership Changes

---

## Security Monitoring

- Top Failed Usernames
- Top Successful Users
- Most Active Workstations
- Logon Types
- Authentication Timeline

---

## System Activity

- Windows Service Activity
- System Events
- Application Events
- Event Volume Over Time

---

## Threat Hunting

- After Hours Logins
- Failed Logins by Computer
- Failed Logins by Username
- Top Event IDs
- Recent Authentication Failures

---

## Alert Monitoring

- Triggered Alerts
- Brute Force Detection
- Excessive Login Failures
- Recent Alert Activity

---

### Dashboard Screenshot

*(Insert your completed Splunk dashboard here.)*

```
images/dashboard-overview.png
```

---

### Alert Screenshot

*(Insert your scheduled brute force detection alert.)*

```
images/brute-force-alert.png
```

---

# Key Takeaways

- Successfully deployed Splunk Enterprise on an Ubuntu Server.
- Configured Windows Server to forward Security, System, and Application logs using the Splunk Universal Forwarder.
- Collected and indexed Windows Event Logs into a custom Splunk index.
- Developed SPL searches to investigate authentication events and identify suspicious activity.
- Built security dashboards to visualize login behavior and Windows event activity.
- Configured scheduled alerts to automate brute force detection.
- Gained practical experience with enterprise SIEM workflows commonly used by SOC analysts and incident responders.

---

## Portfolio Summary

This project demonstrates foundational Security Operations Center (SOC) skills by implementing an end-to-end SIEM solution capable of collecting, searching, visualizing, and monitoring Windows security events.

The lab showcases experience with centralized logging, Windows event analysis, SPL query development, dashboard creation, and automated alerting—core responsibilities found in modern cybersecurity and blue team environments.

**Technologies Used**

- Splunk Enterprise
- Splunk Universal Forwarder
- Ubuntu Server
- Windows Server 2022
- Active Directory
- Windows Event Logs
- SPL (Splunk Processing Language)
- SSH
- Linux CLI

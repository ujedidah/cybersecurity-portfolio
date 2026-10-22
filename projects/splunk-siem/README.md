# Splunk Enterprise: Security Monitoring and Threat Detection

## Project Overview

This project documents my hands-on work deploying Splunk Enterprise, configuring log ingestion, developing Search Processing Language (SPL) queries, and building security dashboards for authentication monitoring and web traffic analysis.

The project explored how centralized logging and security visualizations can support suspicious-activity detection, investigation, and security monitoring workflows.

## Objectives

- Deploy Splunk in a Linux environment.
- Configure log forwarding and validate data ingestion.
- Analyze SSH authentication events.
- Simulate repeated failed SSH login attempts to test detection and monitoring.
- Develop SPL queries for searching, filtering, correlating, and summarizing events.
- Build dashboards for SSH authentication and Apache web traffic.
- Explore how security telemetry supports investigation and incident triage.

## Environment and Tools

- **SIEM:** Splunk Enterprise
- **Operating system:** Ubuntu Linux
- **Initial lab environment:** Kali Linux virtual machine
- **Log collection:** Splunk Universal Forwarder
- **Authentication log source:** `/var/log/auth.log`
- **Web log source:** Apache HTTP Server access logs
- **Query language:** Splunk Search Processing Language (SPL)
- **Visualization:** Splunk dashboards and IP geolocation

The lab was initially deployed on a local Kali Linux virtual machine. Resource constraints on a laptop with 8 GB of RAM led me to migrate the environment to an Ubuntu virtual machine hosted on Layer3Cloud.

## Implementation and Investigation

### 1. Deployment and Log Ingestion

I installed and configured Splunk in the Ubuntu environment and set up log forwarding. I enabled monitoring of Linux authentication logs and validated that authentication events were reaching Splunk for analysis.

### 2. SSH Authentication Monitoring

I analyzed SSH authentication events to examine successful and failed logins, invalid usernames, login activity by username, and source IP addresses.

To validate the monitoring setup, I generated repeated failed SSH login attempts in a controlled test. I then used Splunk to review the resulting events and verify that the relevant activity was visible.

The exercise demonstrated how authentication logs can support the investigation of repeated login failures and potential brute-force activity.

### 3. SSH Authentication and Brute-Force Dashboard

I developed a dashboard to summarize SSH authentication activity and make potentially suspicious patterns easier to investigate.

Dashboard features included:

- Total SSH authentication events
- Successful versus failed login attempts
- Invalid-user activity
- Failed logins grouped by username
- Potential brute-force activity grouped by source IP
- Geographic visualization of source IP addresses

The dashboard was designed to improve visibility into authentication behavior and help identify activity that may require further investigation.

### 4. Apache Web Traffic Analysis

I also developed a dashboard using Apache HTTP Server access logs to explore web traffic patterns and server responses.

Dashboard features included:

- Total HTTP requests
- HTTP response-code distribution
- Client-side errors (4xx)
- Server-side errors (5xx)
- Frequently requested URIs
- Top client IP addresses
- IP geolocation and geographic traffic visualization

This analysis explored how web access logs can help identify unusual request patterns, error spikes, and activity that warrants further investigation.

### 5. SPL Query Development

I developed and refined SPL queries to search, filter, aggregate, correlate, and visualize events from raw log data.

This work strengthened my understanding of transforming raw telemetry into structured information that supports security monitoring and investigation.

## Security Operations Relevance

This project demonstrates practical experience relevant to:

- SIEM deployment and log ingestion
- Authentication monitoring and suspicious-login analysis
- Detection testing using controlled simulated activity
- Web server log analysis
- Detection-oriented query development
- Dashboard design and security visualization
- Initial investigation and triage of potentially suspicious events

Dashboard alerts and unusual patterns are investigation leads, not automatic proof of compromise. Additional context and corroborating evidence are needed before concluding that an incident has occurred.

## Key Takeaways

This project strengthened my practical understanding of SIEM operations, Linux authentication logging, SSH brute-force detection concepts, SPL query development, web traffic analysis, and security dashboard design.

It also reinforced the importance of validating log ingestion, interpreting events in context, and presenting security data in a format that supports timely investigation.

## Evidence and Documentation

<img width="1280" height="548" alt="SSH LOGS" src="https://github.com/user-attachments/assets/aa18f9c6-1435-4ffc-a134-c177d577b079" />
<img width="1280" height="565" alt="image" src="https://github.com/user-attachments/assets/1b98f5c6-0c85-4493-b7e7-7eda3465ffc4" />
<img width="1280" height="402" alt="image" src="https://github.com/user-attachments/assets/29283bd3-411f-45d6-928c-8235c92bb5dd" />
<img width="1280" height="388" alt="image" src="https://github.com/user-attachments/assets/3e6348e5-9e7a-4d15-b470-97e96f5594f5" />
<img width="1280" height="502" alt="image" src="https://github.com/user-attachments/assets/76c344a8-5663-43f2-945f-e94f0b911686" />

## Project Status

This page documents work completed in a previous lab environment. The original environment is no longer available. The project description reflects the work performed, while any supporting screenshots or artifacts will be added only if they are available and safe to share.

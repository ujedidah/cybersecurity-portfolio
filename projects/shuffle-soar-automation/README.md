# SOAR Automation with Shuffle: Alert Enrichment and Incident Notification

## Project Overview

Security Operations Centre (SOC) teams handle large volumes of alerts and log events. Collecting these events is only the first step; enriching them with useful context and delivering actionable information to analysts are equally important.

This project documents two Security Orchestration, Automation and Response (SOAR) workflows built with **Shuffle**. The workflows demonstrate automated alert processing, threat intelligence enrichment, and security notification.

- **Workflow 1:** EDR alert retrieval, parsing, and automated notification.
- **Workflow 2:** Port scan detection using Graylog, IP enrichment through OpenCTI and VirusTotal, and alert delivery to Microsoft Teams.

The goal is to reduce repetitive manual tasks and provide analysts with relevant context to support investigation and response.

## Objectives

- Automate the processing of security alerts.
- Retrieve and structure relevant alert information.
- Enrich suspicious IP addresses with threat intelligence.
- Integrate security tools and communication platforms.
- Apply least-privilege principles to API access.
- Improve the speed and consistency of SOC alert triage.

## Tools and Technologies

| Tool | Purpose |
|---|---|
| Shuffle SOAR | Workflow orchestration and automation |
| EDR API | Retrieve endpoint security alert information |
| Graylog | Collect, search, and analyze logs; define detection events |
| OpenCTI | Retrieve threat intelligence and observable context |
| VirusTotal API | Check available IP reputation and detection information |
| Microsoft Teams | Deliver structured security notifications |

## Workflow 1: EDR Alert Automation

### Overview

This workflow integrates an EDR API with Shuffle to automate the processing of endpoint security alerts and send relevant information to a selected communication channel.

### Workflow Process

1. **Alert retrieval:** Connect to the EDR API to retrieve relevant alert information.
2. **Data processing:** Parse and organize key alert fields into a structured format.
3. **Context preparation:** Prepare the extracted details for notification.
4. **Automated notification:** Dispatch the processed alert information to the configured communication channel.

### Security Controls

The integration uses scoped, read-only API access to follow the principle of least privilege. API tokens, credentials, internal endpoints, and sensitive alert data must not be published in this repository.

## Workflow 2: Graylog Port Scan Detection and Threat Intelligence Enrichment

### Overview

This workflow connects Graylog, Shuffle, OpenCTI, VirusTotal, and Microsoft Teams to detect potential port-scanning activity, enrich the source IP address, and deliver a structured notification to analysts.

### Detection Logic

A custom Graylog event definition uses filter and aggregation conditions to identify a single external source IP contacting **more than 15 distinct destination ports on internal cloud hosts within a five-minute window**.

This pattern can indicate automated scanning or network probing. It is a detection signal for further investigation, not definitive proof of malicious activity.

### Workflow Process

1. **Log monitoring and detection — Graylog:** Evaluate incoming log events and trigger the configured event when the detection conditions are met.
2. **Workflow orchestration — Shuffle:** Receive the event and coordinate the enrichment steps.
3. **Threat intelligence lookup — OpenCTI:** Query available observable records, STIX relationships, and relevant Shadowserver report references.
4. **Reputation check — VirusTotal:** Retrieve available IP-related detection counts and reputation information through the API.
5. **Alert formatting:** Combine the available event and enrichment details into a structured notification.
6. **SOC notification — Microsoft Teams:** Deliver the information using an Adaptive Card so analysts can review the alert context in one place.

### Information Presented to Analysts

Depending on the available source data and enrichment results, the notification can include:

- Source IP address and detection details.
- The event that triggered the workflow.
- Available OpenCTI observable and relationship context.
- Relevant threat intelligence report references.
- VirusTotal detection and reputation information.
- A concise summary to support triage and further investigation.

Enrichment results provide context for analyst review; they do not independently confirm that an IP address is malicious.

## Security Operations Relevance

These workflows demonstrate practical SOC automation concepts:

- **Alert triage:** Organizing relevant details before an analyst begins an investigation.
- **Threat intelligence enrichment:** Adding external context to potentially suspicious indicators.
- **Detection engineering:** Using defined conditions to identify activity that warrants review.
- **Security integrations:** Connecting log management, endpoint security, threat intelligence, orchestration, and notification tools.
- **Least privilege:** Restricting API access to the permissions required for the workflow.
- **Operational efficiency:** Reducing repetitive lookups and manual copying of alert details.

## Challenges and Improvements

The enrichment workflow is being developed further to include additional useful context in the Teams notification.

Potential improvements include:

- Adding more relevant enrichment fields to the Adaptive Card.
- Handling API errors, rate limits, and missing enrichment results.
- Improving event deduplication and notification quality.
- Recording workflow execution outcomes for troubleshooting.
- Refining detection conditions to reduce unnecessary alerts.
- Documenting validation and testing results.

## Evidence and Documentation

<img width="1280" height="564" alt="image" src="https://github.com/user-attachments/assets/9d69ae4e-dd2a-48ce-8d5a-eb5f2579db0c" />
<img width="1068" height="513" alt="image" src="https://github.com/user-attachments/assets/32ccb698-cdc8-4fc0-b1ff-e72e456a45bf" />



This project demonstrates two automation use cases: EDR alert processing and notification, and Graylog-triggered port scan enrichment using OpenCTI and VirusTotal.


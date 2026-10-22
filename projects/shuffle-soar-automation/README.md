# SOAR Automation with Shuffle: EDR Alert Enrichment and Notification

## Project Overview

This project involved building a security automation workflow using Shuffle, an open-source Security Orchestration, Automation, and Response (SOAR) platform.

The workflow integrated an Endpoint Detection and Response (EDR) platform's API with Shuffle to process alert information and dispatch relevant context to a configured communication channel.

The objective was to reduce repetitive manual steps involved in reviewing alerts and make relevant information available to analysts more efficiently.

## Objectives

- Integrate an EDR platform with Shuffle through an API.
- Apply least-privilege principles when configuring API access.
- Use scoped, read-only access tokens for the integration.
- Parse and organize relevant alert information.
- Automate delivery of alert context to a selected communication channel.
- Explore how SOAR workflows can support security operations.

## Tools and Techniques

- **SOAR platform:** Shuffle
- **Security integration:** EDR platform API
- **Authentication:** Scoped, read-only API token
- **Workflow techniques:** API integration, data parsing, workflow orchestration, automated notification
- **Security principle:** Least privilege

## Workflow Overview

### 1. Alert Retrieval

The workflow connected to an EDR platform's API to retrieve relevant alert information using authorized, read-only access.

### 2. Alert Data Processing

Shuffle processed the returned data to extract and organize useful alert context for downstream actions.

### 3. Automated Notification

The workflow dispatched the selected alert information to a configured communication channel, reducing the need to manually navigate between security tools to obtain initial context.

### 4. Access Control

The integration used a scoped, read-only token to limit the permissions required by the workflow, following the principle of least privilege.

## Security Operations Relevance

This project demonstrates practical experience with:

- Security workflow orchestration
- API-based integration between security tools
- Automated alert processing and notification
- Least-privilege access design
- Reducing repetitive analyst tasks
- Improving the availability of alert context for investigation

Automation supports analyst efficiency, but it does not replace the need for human review, validation, and appropriate incident-response decisions.

## Key Takeaways

This project strengthened my understanding of SOAR workflows, API integration, security data processing, automated notifications, and secure credential scoping.

It also demonstrated how carefully designed automation can reduce repetitive operational tasks while maintaining controlled access to security platforms.

## Evidence and Documentation

<img width="1280" height="564" alt="image" src="https://github.com/user-attachments/assets/cec29910-16a9-41bc-8088-e50ce7b8c1d0" />


## Project Status

This page summarizes the workflow I built. Supporting screenshots and technical details will be included where available and authorized for publication.

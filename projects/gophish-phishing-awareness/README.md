# GoPhish Phishing Awareness Simulation

## Project Overview

Designed and supported an authorized phishing awareness simulation using **GoPhish**, covering email template development, email delivery configuration, landing-page hosting, and user awareness education.

The project explored how email security controls affect simulation delivery and how campaign infrastructure can be separated from externally accessible components.

## Tools and Technologies

- **GoPhish** — phishing campaign management
- **HTML** — responsive email template development
- **Microsoft Defender for Office 365** — email security and anti-spoofing controls
- **Exchange mail-flow configuration** — Inbound Connectors and Advanced Delivery policies
- **HTTPS** — secure landing-page delivery
- **Internal lab infrastructure** — GoPhish server hosting

## Technical Implementation

### 1. Email Template Development
- Created a corporate-style HTML email template with signature graphics and embedded images.
- Considered responsive layouts and email-client rendering differences.
- Designed the message to support a realistic, authorized awareness exercise.

### 2. Email Delivery and Security Controls
- Worked with an approved sender-identity structure to support campaign delivery.
- Encountered Microsoft Defender for Office 365 anti-spoofing and identity protections.
- Worked with Exchange Inbound Connectors and Advanced Delivery policies in the authorized environment.
- Considered the interaction between mail-flow configuration and email security controls.

### 3. Infrastructure and Landing Page
- Hosted the GoPhish campaign server on internal lab infrastructure without direct public internet access.
- Hosted the landing page externally over HTTPS.
- Separated campaign management from the participant-facing landing page.

**Workflow:**

```text
GoPhish Server
      |
      v
Campaign Email
      |
      v
Participant Interaction
      |
      v
HTTPS Landing Page
      |
      v
Security Awareness Education
```

### 4. Awareness and Security Considerations
The landing page supported immediate, constructive education when participants interacted with the simulation.

Security considerations included restricting access to campaign infrastructure, protecting sensitive mail-flow settings, and avoiding the publication of participant information or confidential configuration details.

## Skills Demonstrated

- GoPhish campaign management
- HTML email template development
- Email security and anti-spoofing concepts
- Microsoft 365 and Exchange mail-flow concepts
- HTTPS and landing-page deployment
- Infrastructure separation
- Phishing awareness and security documentation

## Outcome

Gained practical experience with the technical components of an authorized phishing awareness simulation, from email-template engineering and delivery considerations to landing-page deployment and user education.

*Disclaimer: Sensitive infrastructure details, production configurations, and participant information are excluded from this public documentation.*

# Phishing Investigation & Response Guide

## Overview
This guide outlines the step-by-step process for investigating suspected phishing emails and initiating appropriate response actions. It’s designed for use by SOC analysts, IT support teams, or managed service providers (MSPs) and aligns with frameworks such as NIST 800-61 and ISO/IEC 27035.

> ⚠️ **Note:** Steps may vary depending on your organization's environment, email filtering tools, and investigation platforms. Adjust accordingly to match your setup.

---

## Investigation Workflow

1. **Initial Report**
   - A user reports a suspicious email via email, helpdesk, or internal alert mechanism.
   - Document the report with as much context as possible (sender, subject line, time received, etc.).

2. **Collect the Email**
   - Retrieve the original email in full, including headers.
   - Export the email as `.eml` or `.msg` if needed for further sandbox analysis.

3. **Header Analysis**
   - Use an email header analyzer or manually inspect the `Received` lines to track email origin.
   - Pay close attention to `Reply-To`, `Return-Path`, SPF/DKIM/DMARC results.

4. **Link and Attachment Inspection**
   - Do **not** click links in a production environment.
   - Use tools such as:
     - [VirusTotal](https://www.virustotal.com/)
     - [URLscan.io](https://urlscan.io/)
     - [Any.Run](https://any.run/) (for sandbox analysis)
   - Submit attachments to sandbox environments (Defender for Office 365, Palo Alto WildFire, etc.)

5. **User Impact Assessment**
   - Determine if the user clicked any links or opened attachments.
   - Check logs for:
     - Endpoint alerts (EDR tools)
     - Browser history
     - Credential submission or sign-in attempts

---

## Containment & Response

1. **Block Indicators**
   - Add sender address, domains, URLs, or hashes to:
     - Email filters (Microsoft Defender, Mimecast, etc.)
     - Firewall or proxy blocklists
     - EDR blacklists

2. **Reset Credentials (If Needed)**
   - If credential compromise is suspected:
     - Reset user password.
     - Revoke active sessions (O365, Google Workspace, etc.)
     - Enforce MFA.

3. **Notify Affected Parties**
   - Inform the user of findings and any actions taken.
   - Escalate if other users received similar emails.

---

## Post-Incident Actions

- **Document the Incident**
  - Summarize findings, IOCs, user impact, and remediation steps.

- **Report to Threat Intel**
  - Share IOCs with your threat intel provider or platform.

- **Awareness & Training**
  - Use the incident as a training opportunity.
  - Consider sending a simulated phishing campaign using the real example.

---

## References

- [NIST SP 800-61 Rev. 2 – Computer Security Incident Handling Guide](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-61r2.pdf)
- [ISO/IEC 27035 – Information Security Incident Management](https://www.iso.org/standard/73499.html)

---

*Maintained by Mike Costner – Security Playbooks & Procedures Project.*

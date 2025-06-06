# Insider Threat – Identification & Response Guide

## Overview
This guide provides a tactical, step-by-step approach to identifying and responding to insider threat activity. Whether malicious or unintentional, insider threats can cause significant damage and are often more difficult to detect than external attacks.

## Objective
To detect, investigate, and respond to suspicious user behavior or unauthorized internal activity that may indicate data exfiltration, sabotage, or policy violations.

---

## 🔍 Step 1: Initial Detection

- Monitor for anomalous user activity via SIEM alerts, DLP systems, or behavioral analytics.
- Common indicators:
  - Accessing large volumes of sensitive files
  - Logging in at odd hours or from unusual locations
  - USB storage or file transfer activity
  - Policy violations logged by endpoint protection software

---

## 📂 Step 2: Containment

- Immediately disable the user’s account or isolate their device from the network (based on severity).
- Notify HR or legal departments if applicable.
- Capture volatile evidence if safe to do so (e.g., memory, active sessions).

---

## 🔎 Step 3: Investigation

- Review logs: authentication, file access, system events.
- Check communication patterns (e.g., email forwarding rules, suspicious file sharing).
- Correlate DLP alerts with user actions and known data assets.
- Interview witnesses or managers (if internal HR protocol allows).

---

## 🧩 Step 4: Determine Scope & Intent

- Identify what systems or data were accessed.
- Determine whether actions were malicious, negligent, or accidental.
- Assess whether sensitive data was exfiltrated or altered.

---

## 🛡️ Step 5: Remediation

- Revoke access and rotate credentials for affected systems.
- Restore modified or deleted data from backups.
- Apply compensating controls to prevent recurrence.
- Update policies and train employees based on findings.

---

## 📝 Documentation & Reporting

- Document the full timeline of events and actions taken.
- Provide a report to internal stakeholders and legal if required.
- Prepare user awareness content to reduce risk of future incidents.

---

## Reference Frameworks

- NIST 800-53 (AU, IR, AC)
- ISO/IEC 27001:2013 (A.7.1.2, A.12.4, A.16)

---

*Maintained by Mike Costner – Security Playbooks & Procedures Project.*

[← Back to Home](https://mcostner.github.io/)

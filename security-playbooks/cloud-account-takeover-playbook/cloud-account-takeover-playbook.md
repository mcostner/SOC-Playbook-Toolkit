# ☁️ Cloud Account Takeover – Response Playbook

**Last Updated:** June 2025  
**Use Case:** Detection and response for unauthorized access to cloud accounts such as Microsoft 365, Google Workspace, or other SaaS platforms.

---

## 🎯 Purpose

This playbook outlines a repeatable process for identifying and responding to cloud account takeovers. It’s designed to support small to mid-sized organizations and aligns with best practices from **NIST CSF (ID.RA, PR.AC, DE.CM, RS.RP)** and **ISO/IEC 27001: A.16, A.12.4**.

---

## 🧩 Indicators of Compromise (IoCs)

- Suspicious login attempts from unfamiliar geolocations or IPs
- MFA prompts or fatigue attacks reported by users
- Inbox rules forwarding to external addresses
- Unexpected device registrations
- Audit logs showing token refresh failures or anomalous API calls

---

## 🔍 Detection & Initial Triage

1. **SIEM/Cloud Logs Review**
   - Check login anomalies in M365/Azure AD sign-in logs or Google Admin logs
   - Look for impossible travel or legacy auth usage
2. **User Reports**
   - Confirm if user experienced unusual prompts or unauthorized actions
3. **Mailbox Rule Review (M365)**
   - PowerShell: `Get-InboxRule` for suspicious forwarding or deletions

---

## 🚨 Containment Steps

- **Immediately disable or suspend the affected account**
- **Revoke all active sessions/tokens**
  - M365: `Revoke-AzureADUserAllRefreshToken`
  - Google Workspace: Admin Console → User → Sign out of all sessions
- **Reset password and force reauthentication**
- **Temporarily disable any suspicious mailbox rules or access delegations**
- **Check for admin privilege abuse**

---

## 🛠️ Eradication & Recovery

- Review and remove persistence mechanisms (OAuth grants, forwarding rules, etc.)
- Check for any secondary accounts affected
- Perform a full mailbox and drive audit for data access/export events
- Restore settings where appropriate
- Re-enable MFA if it was bypassed or disabled

---

## 🔏 Post-Incident Actions

- Conduct user awareness session
- Rotate administrative credentials if there’s any doubt
- Review Conditional Access or equivalent policies
- Enable logging for sensitive operations if not already configured
- Update detection rules or SIEM use cases for future prevention

---

## 📑 Documentation & Reporting

- Timeline of events
- List of impacted assets/accounts
- Root cause (e.g., token theft, MFA fatigue)
- Remediation steps taken
- Recommendations for improving controls

---

## 🔗 Reference Frameworks

- **NIST CSF**
  - **DE.CM-1:** Monitor for unauthorized access
  - **RS.RP-1:** Execute response plan
  - **PR.AC-1:** Identity management & access control
- **ISO/IEC 27001**
  - **A.16.1.5:** Response to information security incidents
  - **A.12.4:** Logging and monitoring

---

## 🧠 Notes

- Cloud takeovers are often precursors to **Business Email Compromise (BEC)** and **data exfiltration.**
- Always assume lateral movement is possible.
- Consider preserving logs for forensic retention.

[← Back to Home](https://mcostner.github.io/)

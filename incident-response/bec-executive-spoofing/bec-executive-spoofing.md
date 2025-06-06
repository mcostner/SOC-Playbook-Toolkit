# Business Email Compromise (BEC) – Executive Spoofing Simulation

## Summary
This case study simulates a Business Email Compromise (BEC) attack targeting a small business finance department. A threat actor impersonates the CEO and attempts to initiate a fraudulent wire transfer via a spoofed email.

## Scenario
- An email appearing to be from the CEO is sent to the finance manager requesting an urgent wire transfer to a “new vendor.”
- The email uses a spoofed display name and domain typo to bypass basic user awareness.
- The message requests secrecy and urgency to increase pressure.

## Detection
- User-reported suspicious tone and incorrect domain.
- Alert triggered in Microsoft Defender for Office 365 (Safe Links/Impersonation Protection).
- Audit logs reviewed for sender origin, IP address, and email header anomalies.

## Triage Steps
1. Verified email header and identified external domain mismatch.
2. Queried mail trace to confirm no additional users were targeted.
3. Conducted keyword search in mailbox for similar patterns or prior attempts.
4. Exported and preserved email for recordkeeping.

## Containment & Response
- Blocked sender and domain at the mail gateway level.
- Created and applied a mail flow rule to warn on display name spoofing.
- Issued internal alert to staff about the attempt with guidance.
- Reviewed SPF, DKIM, and DMARC records to ensure enforcement.

## Lessons Learned
- Implemented external sender banner for increased visibility.
- Conducted targeted security awareness training for the finance team.
- Scheduled monthly phishing simulation campaigns with realistic scenarios.

## Tools Used
- Microsoft Defender for Office 365
- Microsoft Purview (Message Trace, Audit Logs)
- Microsoft Exchange Admin Center
- SPF/DKIM/DMARC validation tools

---

*This is a lab-based recreation of a real-world BEC tactic intended to demonstrate detection and response workflows.*

[← Back to Home](https://mcostner.github.io/)

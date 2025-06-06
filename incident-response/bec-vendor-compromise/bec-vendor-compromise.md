# Business Email Compromise (BEC) – Vendor Payment Diversion

## Summary
This simulated incident recreates a Business Email Compromise (BEC) scenario where a threat actor compromises a trusted vendor’s mailbox and manipulates an active invoice conversation to divert a payment. This type of attack often bypasses technical controls by exploiting trust and timing.

## Scenario
- An accounts payable clerk receives a reply to an ongoing thread with a vendor, requesting that the upcoming payment be sent to a newly provided bank account.
- The email comes from a legitimate domain and known contact, with proper threading and historical context.
- The language is slightly off and includes urgency: "Please process this by end of day to avoid late fees."

## Detection
- The finance team becomes suspicious due to the urgent tone and last-minute account change.
- IT performs an email header analysis and traces the message origin to a foreign IP address (Nigeria-based).
- Microsoft Defender flags the message due to abnormal sender behavior and newly observed sign-in location.

## Triage Steps
1. **Header Review:** Valid sender domain but originating IP is unexpected and geolocated outside the vendor’s normal operations.
2. **Message Trace:** Confirmed delivery only to finance contact, no blast or phishing behavior.
3. **Vendor Contact:** Direct phone call reveals vendor was unaware of the email; confirms compromise.
4. **Mailbox Audit:** Evidence of legacy authentication and no MFA on vendor account.
5. **Log Preservation:** Exported headers, Defender alert, and Purview audit trail.

## Containment & Response
- Blocked the specific sender IP and added domain to conditional mail flow rules.
- Reported incident to the vendor's IT team; advised MFA and password resets.
- Initiated anti-fraud alert with the bank (payment was delayed just in time).
- Internal policy updated: all account changes must be verified via phone, regardless of sender.
- Mail flow rules updated to tag emails with key phrases like “updated banking” or “ACH instructions.”

## Lessons Learned
- Vendor compromise can be more dangerous than direct spoofing due to the appearance of legitimacy.
- Even with SPF/DKIM/DMARC, full authentication isn’t enough when the attacker uses a valid account.
- Regular vendor contact review and secure communication policies are critical in finance workflows.

## Tools Used
- Microsoft Defender for Office 365 (Threat Explorer, Anti-Phishing)
- Microsoft Purview (Audit Logs, Message Trace)
- MxToolbox (Header and DMARC analysis)
- Exchange Admin Center
- Secure bank fraud reporting channel

---

*This is a lab-based recreation of a real-world BEC tactic involving vendor compromise and payment diversion. The workflow demonstrates practical detection and response techniques applicable to real environments.*


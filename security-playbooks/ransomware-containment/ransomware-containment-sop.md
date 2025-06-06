# 🛑 Ransomware Containment – Standard Operating Procedure (SOP)

This guide outlines immediate actions and step-by-step containment procedures to mitigate a ransomware outbreak within a network environment. These steps are meant to reduce damage, preserve evidence, and support a safe recovery process.

---

## 🔒 Step 1: Contain the Threat

- **Disconnect impacted systems** from the network immediately (Wi-Fi, LAN, VPN).
- **Disable switch ports** where possible to physically isolate affected machines.
- Notify internal teams (SOC, IT, executive leadership).

---

## 🧪 Step 2: Identify Scope

- Use EDR/XDR logs to identify initial infection vector.
- Determine if lateral movement occurred or if domain admin accounts were compromised.
- Search for common ransomware indicators (e.g., shadow copy deletion, file renaming, note drops).

---

## 📤 Step 3: Preserve Evidence

- Avoid rebooting systems.
- Clone or image affected endpoints and servers before remediation.
- Collect logs from firewall, SIEM, endpoint, and mail gateway.

---

## ⛔ Step 4: Stop the Spread

- Disable shared drives and file shares.
- Force logout and disable accounts suspected of being used in the attack.
- Block known command-and-control IPs and domains.

---

## 📣 Step 5: Notify

- Alert key stakeholders and legal/compliance teams.
- Follow your breach notification plan (especially if regulated data is affected).
- Prepare a comms plan for internal teams and possibly customers or partners.

---

## 🔁 Step 6: Begin Recovery (Post-Containment)

- Wipe and reimage infected machines — do NOT trust backups until scanned.
- Patch systems and rotate credentials (especially for privileged users).
- Reintroduce systems to the network only after full validation.

---

## 📋 Step 7: Post-Incident Review

- Conduct a full RCA (root cause analysis).
- Update your IR playbooks and detection rules.
- Implement improvements to EDR, MFA, and segmentation based on lessons learned.

---

_**Note:** Specific steps may vary depending on your organization’s setup, available tools, and compliance requirements. Adapt this SOP to fit your environment._

---

*Maintained by Mike Costner – Security Playbooks & Procedures Project.*

[← Back to Home](https://mcostner.github.io/)

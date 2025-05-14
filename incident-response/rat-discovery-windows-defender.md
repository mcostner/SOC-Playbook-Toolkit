# RAT Discovery via Windows Defender

## Overview

During routine analysis of a workstation, Microsoft Defender detected and quarantined a file later identified as a Remote Access Trojan (RAT). This document outlines the discovery process, investigation steps, and recommended mitigation actions based on best practices.

---

## Detection Method

- **Tool Used:** Microsoft Defender (Windows Security)
- **Detection Name:** _[e.g., Trojan:Win32/Rundas!plock]_
- **Alert Level:** _[e.g., Severe]_
- **Initial Clue:** _[e.g., unexpected alert on a low-activity system]_

> _📸 Screenshot Placeholder:_ Defender threat detection window  
> _(include: threat name, severity, detected file path)_

---

## Indicators of Compromise (IoCs)

- **File Name:** _[e.g., rundll32.exe in unusual location]_
- **Path:** _[e.g., C:\Users\...\AppData\Roaming\...]_
- **Persistence Method:** _[e.g., Registry Run key, Scheduled Task]_
- **Other Clues:** Unusual process behavior, suspicious outbound traffic, unknown services

> _📸 Screenshot Placeholder:_ Suspicious autorun entries or tasks

---

## Triage and Investigation

- Reviewed Event Viewer logs for abnormal login/process activity
- Examined Task Scheduler and Startup entries for persistence mechanisms
- Verified file behavior via Defender history and process inspection
- Confirmed non-legitimate behavior (e.g., remote shell callbacks)

> _📸 Screenshot Placeholder:_ Timeline of events, Windows Defender history  
> _📸 Screenshot Placeholder:_ Quarantined item info

---

## Containment and Recommended Mitigation

- Ensure Windows Defender definitions are up to date
- Quarantine or delete the file using Windows Defender or PowerShell
- Disable or delete unauthorized Scheduled Tasks and registry Run keys
- Reset local user passwords (especially admin accounts)
- Conduct full offline Defender scan (via Windows Recovery)
- Review lateral movement or external connections via logs

---

## Lessons Learned

- Even with Defender, sophisticated RATs can sit dormant until triggered
- Behavioral monitoring and endpoint visibility are essential
- Visibility into autoruns and scheduled tasks is critical in threat discovery

---

## Suggested Hardening Actions

- Deploy Defender for Endpoint (if available)
- Enable controlled folder access
- Apply application whitelisting on user workstations
- Disable or restrict script execution (PowerShell, WMI)
- Implement regular integrity checks for startup and scheduled task items

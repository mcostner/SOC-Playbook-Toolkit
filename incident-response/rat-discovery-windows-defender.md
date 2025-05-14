# Remote Access Trojan (RAT) Discovery via Windows Defender

## Overview

This document outlines the discovery of a Remote Access Trojan (RAT) using Microsoft Defender. The threat was detected as part of a multi-stage incident involving suspicious script execution and user account discovery activity.

---

## Detection Summary

- **Tool Used:** Microsoft Defender
- **Severity:** Medium
- **Incident:** Multi-stage involving Execution & Discovery
- **Timeline:** Activity observed from December through May

> ![Defender Incident Alert](rat-discovery/images/rat1.png)

---

## Suspicious Activity Timeline

Microsoft Defender identified:

- `wscript.exe` invoking `powershell.exe`
- Execution of suspicious `.ps1` script
- Suspicious user account discovery behavior

> ![Activity Breakdown](rat-discovery/images/rat2.png)

---

## Key Indicator

One specific alert flagged:

```plaintext
wscript.exe performed user account discovery by invoking powershell.exe
```

This behavior is commonly associated with post-exploitation reconnaissance.

> ![User Account Discovery](rat-discovery/images/rat3.png)

---

## Current Status

- Device remains online and active in the environment
- Defender history shows script-based recon still occurring
- Investigation has not yet resulted in containment or isolation

---

## Recommended Actions

- Immediately isolate the affected endpoint
- Perform a full scan and remove unauthorized scheduled tasks
- Review login history, token use, and session persistence
- Apply application whitelisting and PowerShell logging

---

## Next Steps

Additional review will include deeper analysis of:
- The original PowerShell script
- Potential C2 (Command and Control) communication
- Registry-based persistence or autorun methods

---

## Sample Code Analysis (RAT Script)

Below is a decoded summary of the malicious PowerShell code discovered:

- Heavy use of obfuscation to evade detection
- Calls to `wscript.exe` and `powershell.exe`
- Uses ActiveX to execute silently
- Creates a named mutex to avoid multiple executions
- Establishes persistence via Scheduled Task named `jQueryLibrary`
- Collects system data: username, hostname, IP, architecture
- Uses compression and Base64 encoding to exfiltrate data
- Attempts outbound C2 communication to `https://173.90.0.16:443`
- Loads and executes staged payloads using `Invoke-FruityC2`

> This script is a highly flexible and evasive Remote Access Trojan (RAT) built for stealth and control.


---

## Command Observed (Execution Chain)

The following command was identified on the compromised system:

```powershell
cmd.exe /c "echo var wshShell = new ActiveXObject('WScript.Shell');
wshShell.CurrentDirectory = 'C:\Users\<username>\AppData\Roaming';
wshShell.Run('%SystemRoot%\System32\WindowsPowerShell\v1.0\powershell.exe -ExecutionPolicy Bypass -File C:\CSI\module.ps1', 0, false); > C:\CSI:.js"
```

### Breakdown:
- Uses `ActiveXObject(WScript.Shell)` to invoke PowerShell silently
- Sets working directory to `%AppData%\Roaming` (common for malware staging)
- Executes a hidden script (`module.ps1`) using **ExecutionPolicy Bypass**
- Outputs a disguised script file to `C:\CSI:.js`, suggesting **stealth via fake file extension**

This behavior strongly supports the presence of a stealth RAT using script-based execution, likely tied to a persistence mechanism like **Scheduled Tasks** or **registry autoruns**.


---

## Containment and Remediation

Upon discovery, the compromised device was reported, and an incident review report was submitted with recommended actions. While full remediation details are beyond the scope of this document, the detection of RAT activity prompted internal escalation.

**Recommended actions at the time included:**

- Isolating the endpoint from the network
- Reviewing and removing any persistence mechanisms (e.g., Scheduled Tasks, registry autoruns)
- Resetting affected user credentials
- Conducting a full malware scan and endpoint reimage if necessary
- Reviewing Defender alerts and correlating with other endpoints for potential lateral movement

---

## Next Steps

Based on current findings, future analysis could include:

- Inspecting Windows Task Scheduler and registry autoruns for hidden persistence mechanisms
- Reviewing PowerShell event logs and command-line history
- Extracting and analyzing any related hashes or dropped payloads
- Monitoring network traffic for signs of Command and Control (C2) callbacks

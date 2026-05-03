# Windows Threat Detection 2

**Platform:** TryHackMe
**Path:** Windows Security Monitoring
**Module:** 09 — Windows Security Monitoring
**Difficulty:** Medium
**Room Link:** https://tryhackme.com/room/windowsthreatdetection2

---

## What This Room Covers

The first actions attackers take after breaching a Windows host — discovery,
credential theft, data collection, and exfiltration — and how to detect each
phase in Sysmon and Windows event logs.

---

## Key Concepts Learned

**Post-Initial Access is where the real damage happens.**
Getting in is just the first step. An attacker's goal after initial access is
to understand the environment (discovery), find credentials and sensitive data,
collect it, and get it out. This room covers the entire sequence.

**Discovery via native Windows tools — and why it's hard to detect**
The room opened with running `net user Administrator` — a completely legitimate
command — and then finding it in Sysmon logs. This is the challenge: attackers
use built-in Windows tools (net.exe, whoami, tasklist, ipconfig) that are also
used by administrators. Detection requires context: who ran the command, from
which parent process, at what time, in what sequence?

**Malware Discovery Behavior in Sysmon**
The `invoice.pdf.exe` malware chain demonstrated the typical post-execution
discovery sequence attackers automate:
1. `whoami` — who am I running as?
2. `tasklist /v | findstr MsSense.exe` — is MS Defender EDR running?
3. Exfiltrate discovered system data to C2 domain

Checking for EDR before proceeding is a standard evasion technique — if EDR
is detected, the malware may lie dormant or uninstall itself.

**Credential and Data Theft — what attackers actually take**
The room examined what attackers target after getting in:
- Saved browser passwords (Chrome Password Manager — plaintext accessible to the logged-in user)
- SSH keys stored on disk
- Internal documents (network diagrams, architecture docs, credentials files)

These are exactly the files APT36 and similar groups target in their operations
against Pakistani organizations.

**Data Stealer Malware in Sysmon**
The stealer created a staging directory, searched for specific file extensions
(docx, pdf, xlsx), grabbed clipboard content, then exfiltrated to an S3 bucket.
All of this is visible in Sysmon — directory creation, `cmd.exe` with search
flags, PowerShell cmdlet execution, and DNS resolution for the exfil domain.

**Living Off the Land Download Tools**
The room demonstrated four ways to download files in Windows without a browser:
`curl.exe`, `certutil.exe`, PowerShell IWR (Invoke-WebRequest). Each is a
legitimate Windows tool — each is also abused by attackers and malware for
payload delivery. Detecting their use for downloading from external URLs is
a high-value detection rule.

---

## Hands-On Tasks

Investigated an active malware infection on a Windows VM — traced the
`invoice.pdf.exe` execution chain through Sysmon, manually performed
discovery commands to understand how they appear in logs, identified
credentials and sensitive files stored on the system, and traced the
stealer malware's collection and exfiltration behavior.

---

## Task Answers

| Question | Answer |
|---|---|
| Privileged group Administrator belongs to | `Administrators` |
| Image field of net command in Sysmon | `C:\Windows\System32\net.exe` |
| First command invoice.pdf.exe executes | `whoami` |
| Command malware used to check for MS Defender EDR | `cmd /c "tasklist /v \| findstr MsSense.exe \|\| echo No MS Defender EDR"` |
| Domain malware sent discovered data to | `exfil.beecz.cafe` |
| Facebook password saved in Chrome | `nsAghv51BBav90!` |
| Interesting SSH key stored on disk | `thm-access-database.key` |
| Secret PDF explaining TryHackMe's internal network | `thm-network-diagram-2025.pdf` |
| Directory stealer creates | `staging_58f1` |
| Three file extensions malware searches for | `docx, pdf, xlsx` |
| PowerShell cmdlet malware uses for clipboard | `Get-ClipBoard` |
| Domain malware exfiltrates data to | `collecteddata-storage-2025.s3.amazonaws.com` |
| Flag using Chrome browser | `THM{just_use_web_browser}` |
| Flag using curl.exe | `THM{curl_is_cool}` |
| Flag using certutil.exe | `THM{abusing_certutil}` |
| Flag using PowerShell IWR | `THM{power_of_powershell}` |

---

## Key Concepts for SOC Work

**The process tree is the investigation.**
In Sysmon, every process has a parent. `invoice.pdf.exe → cmd.exe → whoami`
tells a story that individual events cannot. Building the full process tree
from Sysmon Event ID 1 (Process Created) is how SOC analysts reconstruct
exactly what an attacker did — in sequence, with full command lines.

**Attackers use S3 and cloud storage for exfiltration specifically because it blends in.**
Traffic to `amazonaws.com` domains is common in most organizations. A stealer
exfiltrating to a specific S3 bucket will not look unusual on a firewall log.
Detection requires DNS resolution logging (to see the full subdomain) and
DLP rules that flag large outbound transfers to cloud storage.

---

## What I Want to Learn Next Based on This

Windows Threat Detection 3 covers persistence — how attackers ensure they
maintain access after reboots, which is the final phase before long-term
dwell time becomes the real threat.

# Windows Threat Detection 1

**Platform:** TryHackMe
**Path:** Windows Security Monitoring
**Module:** 09 — Windows Security Monitoring
**Difficulty:** Medium
**Room Link:** https://tryhackme.com/room/windowsthreatdetection1

---

## What This Room Covers

Common Initial Access techniques attackers use to get into Windows environments —
RDP brute force, phishing attachments, and USB-based malware — and how to detect
each one using Windows event logs.

---

## Key Concepts Learned

**Initial Access is where every incident begins.**
Every major breach — ransomware, data theft, espionage — starts with one of
a small number of initial access techniques. Detecting these early is the highest
impact opportunity in the entire kill chain.

**RDP Brute Force Detection**
RDP exposed to the internet is one of the most targeted attack surfaces globally.
Detection relies on Event ID 4625 (failed logon) volume — hundreds of failures
from one IP in a short window — followed by a successful 4624 with Logon Type 10.
The attacker's real workstation name is logged in the successful 4624 event,
which is a valuable forensic artifact.

**Phishing Attachment Techniques**
This room covered three real-world phishing delivery methods:
- **COM file with misleading extension** — a `.com` executable disguised as a URL
- **LNK file** — shortcut that downloads next-stage malware from a remote URL
- **Double-extension file** — `best-cat.jpg.exe` appears as an image to users with file extensions hidden

These represent the actual techniques used by threat actors including APT36 against
Pakistani targets. Recognizing them on sight is a practical detection skill.

**USB Malware Detection**
Autorun-style USB malware that propagates from drive to drive still appears in
real incidents. Sysmon logs show the exact file path on the USB drive that was
executed, the dropped payload location, and which additional drives it copied to.

**Web Download via Browser — Sysmon Detection**
When a user downloads and executes a malicious file via browser, the Sysmon
process creation chain shows: browser → file creation → user executes archive →
executable launches → malicious DNS query. Each step is traceable.

---

## Hands-On Tasks

Analyzed live event logs on an attached VM across four Initial Access scenarios.
Each scenario required filtering Event Viewer, following the Sysmon process chain,
and identifying specific artifacts left by each attack technique.

---

## Task Answers

| Question | Answer |
|---|---|
| MITRE technique ID for Initial Access via vulnerable mail server | `T1190` |
| Initial Access method relying on opening malicious email attachment | `Phishing` |
| Most actively targeted user by botnets | `Administrator` |
| IP that breached the host via RDP | `203.205.34.107` |
| Real workstation name (hostname) of the threat actor | `DESKTOP-QNBC4UU` |
| Flag from opening Phishing Case 1 COM file | `THM{misleading_extension}` |
| URL malicious LNK downloads next stage from | `http://wp16.hqywlqpa.thm:8000/cgi-bin/f` |
| Name of double-extension file in Phishing Case 3 | `best-cat.jpg.exe` |
| File user downloaded via web browser | `C:\Users\Administrator\Downloads\top-cats.zip` |
| Folder where user unarchived the suspicious file | `C:\Users\Administrator\Pictures` |
| Process ID of launched phishing malware | `5484` |
| Malicious domain the malware tried to connect to | `rjj.store` |
| USB file launched by user | `E:\Open Sandisk 4GB USB.exe` |
| Suspicious file dropped to disk by USB malware | `C:\Users\Public\Documents\winupdate.exe` |
| USB drive malware propagated to | `F:` |

---

## Key Concepts for SOC Work

**The double-extension trick is still widely used.**
`best-cat.jpg.exe` shows as `best-cat.jpg` when Windows hides file extensions
(the default setting for most users). Enabling "Show file extensions" in
Explorer settings is a basic hardening step — and detecting files with
double extensions in Sysmon file creation events is a high-value detection rule.

**The attacker's workstation name in RDP logs is underutilized intelligence.**
Most analysts look at the source IP of an RDP breach. Fewer check the workstation
name field in the successful 4624 event — but that field contains the attacker's
actual machine hostname, which can be pivoted on across other incidents.

---

## What I Want to Learn Next Based on This

Windows Threat Detection 2 covers what happens after Initial Access —
discovery, credential theft, and data exfiltration — which are the
kill chain phases that cause the most damage.

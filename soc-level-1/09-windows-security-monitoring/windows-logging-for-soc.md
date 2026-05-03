# Windows Logging for SOC

**Platform:** TryHackMe
**Path:** Windows Security Monitoring
**Module:** 09 — Windows Security Monitoring
**Difficulty:** Easy
**Room Link:** https://tryhackme.com/room/windowsloggingforsoc

---

## What This Room Covers

How Windows event logging works, where to find the most important logs,
and how SOC analysts use Security, Sysmon, and PowerShell logs to detect
real attacks.

---

## Key Concepts Learned

**Windows logs everything — but not equally.**
There are over 500 Security event IDs alone. The skill is knowing which ones
matter and what they indicate. This room focused on the highest-value log
sources for daily SOC work.

**The Big Three Log Sources**

| Log Source | Location | Key Use |
|---|---|---|
| Security Event Log | `Windows Logs > Security` | Authentication, account changes, privilege use |
| Sysmon | `Applications and Services > Microsoft > Windows > Sysmon` | Process creation, network connections, file events |
| PowerShell History | `C:\Users\<user>\AppData\Roaming\Microsoft\Windows\PowerShell\PSReadLine\ConsoleHost_history.txt` | Commands run by each user |

**Critical Security Event IDs**

| Event ID | Meaning |
|---|---|
| 4624 | Successful logon |
| 4625 | Failed logon |
| 4720 | User account created |
| 4732 | Member added to security group |
| 4688 | Process created (if auditing enabled) |

**Logon Types matter for investigation**
- Logon Type 2 = Interactive (local keyboard login)
- Logon Type 3 = Network (mapped drive, file share)
- Logon Type 10 = RemoteInteractive (RDP) ← most important for attack detection

**Sysmon gives context Windows native logs don't.**
Where a native Security log says "process created," Sysmon shows the full
command line, parent process, file hash, and network connection — all in one
event. This is why Sysmon has become the de facto standard for advanced monitoring.

**PowerShell history survives reboots and captures every command.**
Unlike `Get-History` (session only), the PSReadLine history file persists
indefinitely. Attackers using PowerShell for discovery, download cradles, or
lateral movement leave traces here that are easy to miss if you don't know to look.

---

## Hands-On Tasks

Worked through three real `.evtx` log files on the VM:

**Practice-Security.evtx** — investigated a brute force and RDP compromise:
filtered by Event ID 4625 to find the attacker's IP, identified the successful
RDP login (Logon Type 10), traced the backdoor user creation with Event ID 4720,
and found which privileged groups the attacker added the backdoor account to.

**Practice-Sysmon.evtx** — traced a malware infection from browser download
through execution, C2 connection, and identified the malicious domain.

**PS History on VM** — browsed the PowerShell history files of multiple users
to reconstruct command activity and find a hidden flag.

---

## Task Answers

| Question | Answer |
|---|---|
| Which event ID describes a successful login? | `Security / 4624` |
| Which IP performed a brute force of THM-PC? | `10.10.53.248` |
| Which user was breached? | `Administrator` |
| Logon ID of the malicious RDP login? | `0x183C36D` |
| Which user was created by the attacker? | `svc_sysrestore` |
| Which two privileged groups was the backdoor user added to? | `Backup Operators, Remote Desktop Users` |
| Does the Logon ID field match the previous task? | `Yea` |
| Which web browser does Sarah use? | `Google Chrome` |
| Which file did Sarah download? | `C:\Users\sarah.miller\Downloads\ckjg.exe` |
| Which URL was the file downloaded from? | `http://gettsveriff.com/bgj3/ckjg.exe` |
| Which file was created by the malware for persistence? | `C:\Users\sarah.miller\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup\DeleteApp.url` |
| What C2 server did malware connect to? | `193.46.217.4:7777` |
| Which domain does the malicious IP correspond to? | `hkfasfsafg.click` |
| Which PowerShell command was executed first? | `Get-ComputerInfo` |
| When did the Administrator run the first PS command? | `May 18, 2025` |
| Flag in PowerShell history? | `THM{it_was_me!}` |

---

## Key Concepts for SOC Work

The investigation chain demonstrated in this room — brute force → RDP login →
user creation → group membership change → malware download → persistence → C2 —
is the exact kill chain a SOC analyst reconstructs when investigating a real
Windows intrusion. Every step leaves a specific event ID.

Event ID 4624 and 4625 are the first IDs any Windows SOC analyst memorizes.
Grouping events by Logon ID is how you link related activity across multiple
log entries without losing the thread of an attack chain.

---

## What I Want to Learn Next Based on This

Windows Threat Detection 1 applies these log analysis skills to specific,
named attack techniques — building detection capabilities rather than
just understanding logs in isolation.

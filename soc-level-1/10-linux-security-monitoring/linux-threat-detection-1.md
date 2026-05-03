# Linux Threat Detection 1

**Platform:** TryHackMe | **Path:** Linux Security Monitoring | **Difficulty:** Medium
**Room Link:** https://tryhackme.com/room/linuxthreatdetection1

---
## What This Room Covers
SSH brute force, web application exploitation, and reverse shell execution against Linux — detected through auth.log and auditd process trees.

---
## Key Concepts Learned

**SSH brute force is the most common Linux Initial Access technique.** Botnets continuously scan port 22. Detection in auth.log: hundreds of `Failed password` entries from one IP in a short window — identical to what I've seen in my Metasploitable lab.

**Command injection creates an unexpected process tree.** The TryPingMe app was vulnerable to `127.0.0.1 && whoami`. The resulting auditd tree shows the web app (python) spawning a shell. A web server spawning `whoami` or `bash` is always suspicious regardless of which individual process looks legitimate.

**Process Tree Analysis is the universal Initial Access detection method.** Regardless of technique, the result is always an unexpected process spawning from a legitimate parent. This is the most reliable detection approach because it catches novel techniques that signature-based tools miss.

---
## Task Answers
| Question | Answer |
|---|---|
| When did ubuntu user first SSH in? | `2024-10-22` |
| Did ubuntu use SSH keys? | `Yea` |
| When did SSH brute force start? | `2025-08-21` |
| Four users botnet attempted to breach | `root, roy, sol, user` |
| IP that breached root | `91.224.92.79` |
| Path to Python file attacker opened | `/opt/trypingme/main.py` |
| Flag inside opened file | `THM{i_am_vulnerable!}` |
| PPID of suspicious whoami | `1018` |
| PID of TryPingMe app | `577` |
| Program used to open reverse shell | `python` |
| MITRE technique if trusted app runs malicious commands | `Supply Chain Compromise` |
| Best detection method for Initial Access | `Process Tree Analysis` |

---
## How This Applies to Real SOC Work
Root brute force success is catastrophic — the attacker gets complete control. The better preventive control is disabling root SSH login entirely (`PermitRootLogin no`) and requiring key-based auth. Detection is important, but prevention matters more here.

# Linux Logging for SOC

**Platform:** TryHackMe | **Path:** Linux Security Monitoring | **Difficulty:** Easy
**Room Link:** https://tryhackme.com/room/linuxloggingforsoc

---
## What This Room Covers
The key Linux log sources SOC analysts use — syslog, auth.log, package manager logs, bash history, and auditd — and how to extract security-relevant information from each.

---
## Key Concepts Learned

**Linux Log Sources**
| Linux Log | Windows Equivalent | Key Content |
|---|---|---|
| `/var/log/auth.log` | Security Event Log | SSH logins, sudo, user creation |
| `/var/log/syslog` | System Event Log | Service starts, kernel messages, NTP |
| `/var/log/dpkg.log` | Windows Update Log | Package installs/removals |
| `~/.bash_history` | PowerShell history | Commands run by each user |
| `auditd` | Sysmon | Detailed syscall-level activity |

**grep is the primary Linux log analysis tool.**
Linux logs are plain text files. `grep`, `awk`, `sed`, and pipes are how analysts extract events. `grep "Failed password" /var/log/auth.log` does in one command what Event Viewer needs a filter dialog to achieve.

**auditd — Linux's answer to Sysmon.**
The Linux Audit Daemon captures file opens, process creation, and network connections based on configurable rules. `ausearch` is the query tool. Like Sysmon, it needs configuration — it is not fully useful out of the box.

---
## Task Answers
| Question | Answer |
|---|---|
| Time server domain VM contacted | `ntp.ubuntu.com` |
| Kernel message from Yama in syslog | `Becoming mindful.` |
| IP that failed SSH login on multiple users | `10.14.94.82` |
| User created and added to sudo group | `xerxes` |
| Version of unzip installed | `6.0-28ubuntu4.1` |
| Flag in bash history | `THM{note_to_remember}` |
| Linux syscall commonly used to execute a program | `execve` |
| Can a program bypass system calls? | `Nay` |
| When was secret.thm opened first? | `08/13/25 18:36:54` |
| Original filename downloaded from GitHub | `naabu_2.3.5_linux_amd64.zip` |
| Network range scanned | `192.168.50.0/24` |

---
## How This Applies to Real SOC Work
Linux servers power most of the internet's backend infrastructure — web servers, databases, cloud instances. A SOC analyst who cannot read Linux logs is blind to a significant portion of the attack surface. The auditd finding in this room mirrors exactly what scanning from Kali against Metasploitable generates in my home lab.

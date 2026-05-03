# 🐧 Module 10 — Linux Security Monitoring

> Learn how Linux logging works and how to use it to detect common Linux attacks through real-world examples and hands-on threat detection labs.

**Path Link:** [Linux Security Monitoring](https://tryhackme.com/module/linux-security-monitoring)
**Status:** ✅ Complete | **Rooms:** 4

---

## 📊 Room Index

| Room | Write-up | Key Topic | Difficulty |
|---|---|---|---|
| Linux Logging for SOC | [Link](./linux-logging-for-soc.md) | syslog, auth.log, auditd, bash history | Easy |
| Linux Threat Detection 1 | [Link](./linux-threat-detection-1.md) | SSH brute force, web exploitation, reverse shells | Medium |
| Linux Threat Detection 2 | [Link](./linux-threat-detection-2.md) | Discovery, EDR evasion, cryptominers | Medium |
| Linux Threat Detection 3 | [Link](./linux-threat-detection-3.md) | Reverse shells, privilege escalation, persistence | Hard |

---

## 🔑 Module Summary

Linux servers power most cloud and backend infrastructure. This module applies the same detection methodology from the Windows module to Linux — different log sources and tools, identical attacker TTPs.

**Key log files:** `/var/log/auth.log`, `/var/log/syslog`, `~/.bash_history`, auditd

**Most important takeaway:** Process tree analysis via auditd is as powerful on Linux as Sysmon is on Windows. A web server spawning a shell is suspicious regardless of platform.

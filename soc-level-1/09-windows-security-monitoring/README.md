# 🪟 Module 09 — Windows Security Monitoring

> Learn how Windows logging works and how to use it to detect common Windows attacks through real-world examples and hands-on threat detection labs.

**Path Link:** [Windows Security Monitoring](https://tryhackme.com/module/windows-security-monitoring)
**Status:** ✅ Complete | **Rooms:** 4

---

## 📊 Room Index

| Room | Write-up | Key Topic | Difficulty |
|---|---|---|---|
| Windows Logging for SOC | [Link](./windows-logging-for-soc.md) | Security logs, Sysmon, PowerShell history | Easy |
| Windows Threat Detection 1 | [Link](./windows-threat-detection-1.md) | RDP brute force, phishing, USB malware | Medium |
| Windows Threat Detection 2 | [Link](./windows-threat-detection-2.md) | Discovery, credential theft, data exfiltration | Medium |
| Windows Threat Detection 3 | [Link](./windows-threat-detection-3.md) | C2 implants, persistence, ransomware | Medium |

---

## 🔑 Module Summary

This module builds practical Windows detection skills on top of the SOC Level 1 fundamentals. The four rooms form a complete attack chain — from initial log understanding through detecting Initial Access, post-exploitation, and persistence — using only Windows Event Logs and Sysmon.

**Critical Event IDs covered:** 4624, 4625, 4720, 4732, 4688, 7045, 4698

**Most important takeaway:** Sysmon process trees are the single most valuable artifact for Windows investigation. Every attack leaves a parent-child process chain that tells the full story even when individual events look benign.

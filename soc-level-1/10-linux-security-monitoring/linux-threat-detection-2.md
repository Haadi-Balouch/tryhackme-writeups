# Linux Threat Detection 2

**Platform:** TryHackMe | **Path:** Linux Security Monitoring | **Difficulty:** Medium
**Room Link:** https://tryhackme.com/room/linuxthreatdetection2

---
## What This Room Covers
Post-Initial Access on Linux — discovery scripts, EDR enumeration, credential hunting, download cradles, and cryptominer deployment.

---
## Key Concepts Learned

**Attackers run discovery scripts immediately after getting access.** The `debug.sh` script demonstrated the typical sequence: hostname, system info, `ps -eo pid,ppid,cmd,%mem,%cpu --sort=-%cpu` to profile running processes. This is automated and runs in seconds.

**Checking for EDR is standard attacker practice.** The attacker used `egrep` to search for `ds_agent` (Digital Guardian), `falcon` (CrowdStrike), and `sentinel` (SentinelOne) in process list. If found, the attacker may abort or change approach. This EDR enumeration is visible in auditd.

**Cryptominers hide in `/tmp` using misleading names.** `kernupd.tar.gz` masquerades as a kernel update. The miner launched as `nohup /tmp/.apt/kernupd/kernupd` — `nohup` keeps it running after terminal disconnection, `/tmp/.apt/` mimics a legitimate package manager directory.

**After compromising one host, attackers immediately scan for more.** The IP range `10.10.12.1-10.10.12.10` was scanned for SSH after deploying the miner. Internal-to-internal port scans should always be investigated.

---
## Task Answers
| Question | Answer |
|---|---|
| systemd-detect-virt output | `amazon` |
| Full path to antimalware binary | `/var/lib/ultrasec/malscan` |
| Script that ran hostname command | `/home/itsupport/debug.sh` |
| Last discovery command in script | `ps -eo pid,ppid,cmd,%mem,%cpu --sort=-%cpu` |
| Email of script author | `greg@tryhackme.thm` |
| Domain Elastic agent downloaded from | `artifacts.elastic.co` |
| Full path to helper.sh | `/var/tmp/helper.sh` |
| More suspicious: curl or wget? | `curl` |
| IP that brute-forced SSH | `45.9.148.125` |
| Command to list last logged-in users | `last` |
| Three EDR processes attacker looked for | `ds_agent, falcon, sentinel` |
| Malicious archive transferred via SCP | `kernupd.tar.gz` |
| Cryptominer launch command | `nohup /tmp/.apt/kernupd/kernupd` |
| IP range attacker scanned | `10.10.12.1-10.10.12.10` |

---
## How This Applies to Real SOC Work
Cryptomining is the most common Linux malware payload — it is low-risk for the attacker (not as legally severe as data theft) but causes real business impact through CPU consumption and cloud billing spikes. An alert on anomalously high CPU usage from an unexpected process is often how cryptominers are first detected in cloud environments.

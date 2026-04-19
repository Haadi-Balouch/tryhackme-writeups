# Network Discovery Detection

**Platform:** TryHackMe | **Module:** Network Security | **Difficulty:** Easy
**Room Link:** https://tryhackme.com/room/networkdiscovery

---
## What This Room Covers
How attackers perform network discovery after initial access, and how SOC analysts detect reconnaissance activity in network logs and SIEM data.

---
## Key Concepts Learned
**Network discovery is Phase 2 of the Unified Kill Chain — the attacker is already inside.**
When an attacker lands on their initial host, they immediately begin mapping the internal network: what other hosts exist, what services are running, what credentials they have access to. Detecting this activity is how SOC teams identify active intrusions before the attacker reaches their objective.

**Discovery techniques and their detection signatures**

| Discovery Technique | Tool Used | Detection Signature |
|---|---|---|
| Host discovery (ping sweep) | nmap -sn, ping | ICMP echo requests from one host to many destinations in rapid succession |
| Port scanning | nmap -sS | SYN packets from one host to many ports on one or more targets |
| Service enumeration | nmap -sV | Multiple connection attempts with specific probes to identified open ports |
| DNS enumeration | nslookup, dig | High-frequency DNS queries for internal hostnames |
| SMB enumeration | net view, enum4linux | SMB session establishment to many hosts |
| ARP scanning | arp-scan | ARP requests for many IPs in rapid succession from one host |

**The internal scan is more suspicious than external**
An external Nmap scan against a network perimeter is common — pen testers, vulnerability scanners, and attackers all do this. An internal host conducting a port scan of other internal systems is a much stronger indicator of active compromise or insider threat. Internal-to-internal scanning should always be investigated.

**Baselines enable anomaly detection**
A vulnerability scanner legitimately scans the network on a schedule — this generates detection signatures identical to attacker scanning. The difference is context: authorized scanner on a known schedule during business hours versus unknown host scanning at 3 AM. SIEM rules for discovery detection need to account for authorized scanning activity to avoid false positive noise.

---
## How This Applies to Real SOC Work
Detecting network discovery is detecting the attacker's reconnaissance phase after initial access. Finding this activity early — before lateral movement and privilege escalation — significantly limits the damage scope.

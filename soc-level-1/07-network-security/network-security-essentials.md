# Network Security Essentials

**Platform:** TryHackMe | **Module:** Network Security | **Difficulty:** Easy
**Room Link:** https://tryhackme.com/room/networksecurityprotocols

---
## What This Room Covers
Core network security concepts — secure vs insecure protocols, network segmentation, access controls, and the monitoring approaches that underpin SOC detection.

---
## Key Concepts Learned
**Secure vs insecure protocols — the most operationally important distinction**
| Insecure Protocol | Secure Replacement | Why It Matters |
|---|---|---|
| Telnet (23) | SSH (22) | Telnet sends everything cleartext — credentials visible in packet captures |
| FTP (21) | SFTP / FTPS | FTP credentials transmit unencrypted |
| HTTP (80) | HTTPS (443) | HTTP sessions interceptable — credentials, session tokens exposed |
| SMTP without TLS | SMTP with TLS/STARTTLS | Email contents and credentials exposed |
| SNMPv1/v2 | SNMPv3 | Community strings transmit cleartext |

**Network segmentation as a security control**
Flat networks — where every system can communicate with every other system — are a lateral movement attacker's dream. Segmentation divides the network into zones with controlled inter-zone traffic. A compromised workstation in a segmented network cannot reach the database server directly — the attacker must find a path through the firewall or pivot through an intermediate system. Every extra hop required is another detection opportunity.

**Defense in depth — the principle behind layered security**
No single control is sufficient. Firewalls, IDS, EDR, SIEM, network segmentation, and strong authentication work together. An attacker who bypasses one layer faces the next. The SOC monitors the intersection of all these layers — when something slips through the outer defenses, the SIEM sees it.

---
## How This Applies to Real SOC Work
Understanding what should and should not be on a network makes anomalies obvious. When I see Telnet traffic in a modern network, that is immediately suspicious — Telnet has no legitimate use in a properly managed environment. Baseline knowledge of secure network design is what makes deviations stand out.

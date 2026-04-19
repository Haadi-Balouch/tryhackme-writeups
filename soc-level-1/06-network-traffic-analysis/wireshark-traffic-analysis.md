# Wireshark: Traffic Analysis

**Platform:** TryHackMe | **Module:** Network Traffic Analysis | **Difficulty:** Medium
**Room Link:** https://tryhackme.com/room/wiresharktrafficanalysis

---
## What This Room Covers
Applying Wireshark to real-world traffic analysis scenarios — identifying anomalies, detecting specific attack signatures, and analyzing malicious traffic patterns.

---
## Key Concepts Learned
**This room took significant time — it required connecting all previous Wireshark knowledge under time pressure to find specific evidence in real traffic captures.**

**Anomaly-based analysis approach**
Rather than looking for specific known signatures, anomaly detection asks: what looks different from normal? Unusually large DNS queries, HTTP requests with no user agent, periodic connections at exact intervals (C2 beaconing), plaintext credentials in unencrypted protocols — these stand out against a baseline of normal traffic.

**C2 traffic signatures in Wireshark**
- Regular, periodic connections to the same external host (beacon interval)
- HTTP C2 often uses unusual URI paths, fake User-Agent strings, or encoded data in URL parameters
- DNS C2 uses unusually long domain names or high-frequency queries to unusual domains
- Traffic volume asymmetry — small requests, large responses (data being pulled from victim)

**Data exfiltration signatures**
- Large outbound transfers to external IPs, especially outside business hours
- DNS queries with unusually long subdomains (DNS tunneling — data encoded in subdomain labels)
- ICMP packets with unusually large payloads (ICMP tunneling)
- HTTP POST requests with large bodies to external endpoints

**Real captures = real complexity**
Real traffic is messy — retransmissions, keep-alives, broadcast traffic, and normal application noise all mix with the malicious activity. The filtering and statistics skills from the previous rooms are essential for cutting through noise.

---
## How This Applies to Real SOC Work
The analysis scenarios in this room mirror exactly what a SOC analyst does when examining network evidence from a security incident. Building this pattern recognition — what normal looks like versus what attack traffic looks like — is one of the most valuable skills developed in this entire module.

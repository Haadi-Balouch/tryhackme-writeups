# Man-in-the-Middle Detection

**Platform:** TryHackMe | **Module:** Network Security | **Difficulty:** Medium
**Room Link:** https://tryhackme.com/room/mitmdetection

---
## What This Room Covers
What MITM attacks are, how they are executed, and the network indicators that reveal their presence.

---
## Key Concepts Learned
**A MITM attack makes the attacker invisible in the middle of a legitimate communication.**
The victim thinks they are communicating directly with the server. The server thinks it is communicating directly with the victim. In reality, the attacker intercepts, reads, and potentially modifies everything in between.

**MITM Attack Techniques**

| Technique | How It Works | Detection Indicator |
|---|---|---|
| ARP Poisoning | Sends fake ARP replies to associate attacker's MAC with victim's IP | Duplicate IP-to-MAC mappings in ARP table, unusual ARP reply frequency |
| DNS Spoofing | Returns malicious IP for legitimate domain queries | DNS responses not from authorized DNS servers, IP mismatches for known domains |
| SSL Stripping | Downgrades HTTPS to HTTP | HTTPS sites loading as HTTP, certificate warnings |
| Rogue AP | Sets up a fake WiFi access point | New SSIDs matching legitimate ones, MAC mismatch on AP |
| BGP Hijacking | Announces false routing paths to redirect internet traffic | Route changes for specific IP prefixes, traffic going through unexpected ASNs |

**ARP Poisoning detection in Wireshark**
ARP poisoning is detectable in packet captures:
- Multiple ARP replies claiming different MAC addresses for the same IP
- ARP reply not following an ARP request (unsolicited gratuitous ARP)
- Wireshark will flag "duplicate use of IP address" warnings automatically

**Certificate validation as a MITM defense**
A valid TLS certificate from the correct CA is the primary defense against MITM on HTTPS. SSL inspection in corporate networks introduces intentional MITM — all traffic is intercepted by the proxy, which presents its own certificate. This is legitimate and configured, but demonstrates that MITM is architecturally possible even on "encrypted" connections.

---
## How This Applies to Real SOC Work
MITM attacks on internal networks, particularly ARP poisoning, are realistic threats in environments without dynamic ARP inspection on switches. Network monitoring that alerts on ARP anomalies provides early detection of internal MITM attempts.

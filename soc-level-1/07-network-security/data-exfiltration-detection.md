# Data Exfiltration Detection

**Platform:** TryHackMe | **Module:** Network Security | **Difficulty:** Medium
**Room Link:** https://tryhackme.com/room/dataexfiltrationdetection

---
## What This Room Covers
How attackers exfiltrate data from compromised environments, and the network and log-based signatures used to detect it.

---
## Key Concepts Learned
**Data exfiltration is the attacker's endgame — detecting it means detecting the final objective.**
Everything before exfiltration is setup. The moment data leaves the network, the attacker has achieved their objective. Detecting exfiltration in progress allows containment before the full dataset is lost.

**Exfiltration channels and their detection signatures**

| Channel | How It Works | Detection Approach |
|---|---|---|
| HTTP/HTTPS | POST requests with data in body to external server | Large POST bodies to external IPs, especially new domains |
| DNS tunneling | Data encoded in DNS query subdomains | Abnormally long domain names, high query frequency to one domain |
| ICMP tunneling | Data in ICMP payload | Large ICMP packets (normal ping payload is 32 bytes) |
| FTP/SFTP | Direct file transfer | Outbound FTP to external IPs, especially large transfers |
| Cloud storage | Upload to Dropbox, Google Drive, etc. | Unusual volume of uploads to cloud storage domains |
| Email | Attachments in outbound email | Large outbound email with attachments outside normal patterns |

**DNS tunneling — the hardest to detect**
DNS is almost always allowed outbound because legitimate applications require it.
Attackers exploit this by encoding data in DNS query labels. A normal DNS query is
short: `api.github.com`. A DNS tunneling query might look like:
`YWRtaW46cGFzc3dvcmQ=.evil-domain.com` — base64-encoded data in the subdomain.
Detection requires monitoring DNS query length and frequency, not just destination.

**Baseline-based detection for exfiltration**
Normal outbound data volumes vary by organization. Detecting exfiltration requires
knowing what normal looks like: typical outbound volume per user, per department,
per hour. A sudden 10GB outbound transfer from a host that normally transfers
100MB per day is immediately anomalous. DLP (Data Loss Prevention) systems
enforce these baselines automatically.

---
## How This Applies to Real SOC Work
Data exfiltration detection is one of the highest-stakes SOC responsibilities — finding it quickly limits legal and regulatory exposure. The network signatures from this room are directly implementable as Splunk detection rules in my home lab.

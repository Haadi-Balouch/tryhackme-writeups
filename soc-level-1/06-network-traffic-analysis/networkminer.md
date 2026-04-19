# NetworkMiner

**Platform:** TryHackMe | **Module:** Network Traffic Analysis | **Difficulty:** Easy
**Room Link:** https://tryhackme.com/room/networkminer

---
## What This Room Covers
NetworkMiner — a network forensic analysis tool that automatically reconstructs sessions, extracts files, and organizes artifacts from PCAP captures.

---
## Key Concepts Learned
**NetworkMiner and Wireshark are complementary, not competitive.**
Wireshark lets you examine individual packets in detail. NetworkMiner automatically extracts and organizes everything useful from a capture — hosts discovered, files transferred, credentials observed, messages exchanged. For incident response, NetworkMiner surfaces the key artifacts fast.

**What NetworkMiner extracts automatically from a PCAP**
| Tab | What It Shows |
|---|---|
| Hosts | All hosts discovered in the capture with OS fingerprint |
| Files | Every file transferred — downloadable directly from the tool |
| Images | All images transferred — visual evidence of web browsing or exfiltrated data |
| Messages | Emails, chat messages, and other communications |
| Credentials | Usernames and passwords observed in cleartext protocols |
| Sessions | Summary of all network sessions |

**The Credentials tab is particularly powerful**
Any cleartext protocol — HTTP Basic Auth, FTP, Telnet, POP3, SMTP without TLS —
will expose credentials. In a capture containing Metasploitable traffic, the
Credentials tab immediately shows the msfadmin/msfadmin FTP and Telnet
credentials. In a real incident, this tab can reveal what an attacker captured
or what was inadvertently transmitted unencrypted.

**OS fingerprinting from traffic**
NetworkMiner attempts to identify operating systems from network behavior
(TTL values, TCP window sizes, quirks in protocol implementation). This is
useful in incident response when you need to enumerate what types of systems
were involved in suspicious traffic without access to the systems themselves.

---
## How This Applies to Real SOC Work
NetworkMiner accelerates the evidence collection phase of network forensics. Rather than manually extracting files from a Wireshark capture (which requires knowing exactly which packets to export), NetworkMiner does this automatically. In a fast-moving incident investigation, that speed advantage is significant.

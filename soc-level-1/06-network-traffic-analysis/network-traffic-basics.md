# Network Traffic Basics

**Platform:** TryHackMe | **Module:** Network Traffic Analysis | **Difficulty:** Easy
**Room Link:** https://tryhackme.com/room/networkfundamentals

---
## What This Room Covers
Foundations of network traffic analysis — what network traffic is, how to collect it, and which tools are available for analysis.

---
## Key Concepts Learned
**Network traffic is the most complete record of what happened.** Logs can be deleted, endpoints wiped, but network traffic captured at a tap or span port is the ground truth of what bytes moved between which systems when.

**Traffic collection methods**
| Method | How It Works | Use Case |
|---|---|---|
| Port mirroring (SPAN) | Switch copies traffic to a monitoring port | Inline monitoring on a network segment |
| Network TAP | Physical device that passively copies traffic | High-fidelity capture without impacting network |
| Host-based capture | tcpdump or Wireshark on individual host | Targeted capture on a specific system |
| NetFlow/IPFIX | Flow records — summary data, no payload | High-volume traffic analysis at scale |

**The difference between full packet capture and flow data**
Full packet capture (PCAP) contains everything — headers and payload. It is storage-intensive but complete. NetFlow contains only metadata — source IP, destination IP, port, protocol, bytes transferred. It cannot reconstruct sessions but scales to handle enterprise traffic volumes. SOC analysts use both: NetFlow for pattern detection at scale, PCAP for deep-dive investigation.

**Protocol layers matter for analysis**
Understanding where to look for different attack indicators: Layer 3 (IP) for scanning and routing anomalies, Layer 4 (TCP/UDP) for port-based detection, Layer 7 (application protocols: HTTP, DNS, FTP) for content-based detection. Most interesting SOC findings are at Layer 7.

---
## How This Applies to Real SOC Work
Network traffic analysis is foundational to investigating C2 communication, lateral movement, and data exfiltration — all of which leave network traces even when endpoints are cleaned. Understanding collection methods tells me what data is available and what blind spots exist.

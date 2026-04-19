# Wireshark: Packet Operations

**Platform:** TryHackMe | **Module:** Network Traffic Analysis | **Difficulty:** Medium
**Room Link:** https://tryhackme.com/room/wiresharkpacketoperations

---
## What This Room Covers
Advanced Wireshark features — statistics, filtering operators, protocol dissection, and finding specific patterns in large captures.

---
## Key Concepts Learned
**Finding a needle in a haystack — this is what packet operations is about.**
A real incident capture can contain millions of packets. The skill is getting to the relevant subset fast.

**Statistics tools that changed how I use Wireshark**
- **Statistics → Protocol Hierarchy:** Shows the breakdown of protocols in the capture. An unusually high percentage of one protocol is immediately suspicious.
- **Statistics → Conversations:** Lists all host pairs that communicated, with byte counts. A host communicating with an unknown external IP with significant data transfer is a lead.
- **Statistics → IO Graph:** Visualizes traffic volume over time. A spike at a specific time correlates with when the incident occurred.

**Advanced display filter operators**
| Operator | Use | Example |
|---|---|---|
| `contains` | String match within field | `http.host contains "evil"` |
| `matches` | Regex match | `http.request.uri matches "\.php\?id=[0-9]"` |
| `in` | Match multiple values | `tcp.port in {80 443 8080}` |
| `&&` | AND | `ip.src == 10.0.0.1 && tcp.port == 22` |

**GeoIP — identifying where traffic goes**
Wireshark can be configured to show geographic location of IPs. Traffic going
to unusual geographic locations — especially from servers that should only
communicate internally — is an immediate red flag.

---
## How This Applies to Real SOC Work
The statistics features transform Wireshark from a packet viewer into an investigation accelerator. Rather than manually scrolling through a large capture, statistical analysis identifies anomalies that direct focus to the relevant packets immediately.

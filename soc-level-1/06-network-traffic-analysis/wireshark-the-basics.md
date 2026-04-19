# Wireshark: The Basics

**Platform:** TryHackMe | **Module:** Network Traffic Analysis | **Difficulty:** Easy
**Room Link:** https://tryhackme.com/room/wiresharkthebasics

---
## What This Room Covers
Wireshark fundamentals — interface navigation, packet structure, display filters, and protocol analysis.

---
## Key Concepts Learned
**Wireshark filter syntax was confusing at first — this was one of the harder parts of the network analysis module for me.**
The syntax looks similar to programming but has its own rules. The breakthrough was understanding that display filters use dot notation for nested fields: `tcp.flags.syn` not `tcp syn flags`. Once that clicked, writing filters became much faster.

**The Wireshark interface**
- Packet List (top pane) — one row per packet, high-level summary
- Packet Details (middle pane) — hierarchical breakdown of the selected packet's protocol layers
- Packet Bytes (bottom pane) — raw hex and ASCII of the packet payload

**Essential display filters for SOC use**

| Filter | Purpose |
|---|---|
| `tcp.flags.syn == 1 && tcp.flags.ack == 0` | Port scan detection |
| `http.request.method == "POST"` | Credential submissions or data uploads |
| `dns.qry.name contains "."` | DNS queries — look for C2 domain patterns |
| `ip.addr == X.X.X.X` | Isolate one host |
| `!(arp or dns or icmp)` | Remove background noise |
| `tcp.stream eq N` | Follow a specific TCP session end-to-end |

**Follow TCP Stream**
Right-clicking any packet → Follow → TCP Stream reconstructs the entire
conversation in human-readable form. This is essential for seeing what
was actually communicated — HTTP requests and responses, FTP commands,
plaintext credentials in Telnet sessions. In my home lab, following a
Telnet stream to Metasploitable reveals credentials in cleartext — a
vivid demonstration of why Telnet should never be used.

---
## How This Applies to Real SOC Work
Wireshark is the microscope of network investigation. When a SIEM alert fires for unusual traffic, opening the corresponding PCAP in Wireshark and following the TCP stream shows exactly what the communication contained. That granularity is often what confirms a true positive.

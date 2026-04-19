# Snort

**Platform:** TryHackMe | **Module:** Network Security | **Difficulty:** Hard
**Room Link:** https://tryhackme.com/room/snort

---
## What This Room Covers
Hands-on Snort usage — running Snort in different modes, reading and writing detection rules, and analyzing traffic using Snort's output.

---
## Key Concepts Learned
**Snort was genuinely hard — writing rules was the most technically challenging part of the network security module.**
The syntax is precise and unforgiving. A single misplaced character makes a rule invalid with no useful error message. It took several attempts to write rules that correctly matched what I intended to detect.

**Snort's Three Modes**

| Mode | Command | Use Case |
|---|---|---|
| Sniffer | `snort -v` | Display packets on screen — similar to tcpdump |
| Packet Logger | `snort -l ./logs` | Save packets to log files for later analysis |
| IDS/IPS | `snort -A console -c snort.conf` | Apply rules and generate alerts |

**Snort Rule Structure**
```
[action] [protocol] [src IP] [src port] -> [dst IP] [dst port] ([options])
```

Example — detect SSH brute force:
```
alert tcp any any -> $HOME_NET 22 (msg:"SSH Brute Force Attempt"; \
  threshold:type threshold, track by_src, count 5, seconds 60; \
  sid:1000001; rev:1;)
```

**Rule anatomy breakdown**
- `alert` — action: generate an alert
- `tcp` — protocol
- `any any` — any source IP, any source port
- `-> $HOME_NET 22` — destined for our network on port 22
- `msg:` — alert message string
- `threshold:` — only alert if 5 connections in 60 seconds (reduces noise)
- `sid:` — unique rule identifier
- `rev:` — rule revision number

**The threshold option was the hardest part to get right.**
Writing a threshold rule that fires on genuine brute force (dozens of attempts)
but not on a user mistyping their password twice requires careful tuning.
Too low and legitimate users trigger it. Too high and real attacks slip through.
Rule tuning is an ongoing process, not a one-time setup.

**Snort rule options I used most**
| Option | Purpose |
|---|---|
| `content:"string"` | Match specific string in payload |
| `nocase` | Case-insensitive content match |
| `flags:S` | Match on TCP SYN flag (port scan detection) |
| `threshold:` | Control alert frequency |
| `detection_filter:` | Rate-based filtering |
| `pcre:` | Regex match in payload |

---
## How This Applies to Real SOC Work
Snort rules are the foundation of network-based detection. Understanding how to write and tune them means I can contribute to detection engineering even as an L1 analyst. The skills are directly applicable — Snort is widely deployed in real SOC environments, and the rule writing concepts transfer to other IDS/IPS platforms.

---
## What I Learned the Hard Way
Writing rules without testing them against actual traffic first is pointless. The workflow that worked: capture the attack traffic with tcpdump first, write the rule, run Snort against the PCAP file to verify it fires, then deploy to live monitoring. Testing against a real sample before deployment saved significant debugging time.

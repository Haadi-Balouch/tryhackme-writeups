# Detecting Web DDoS

**Platform:** TryHackMe | **Module:** Web Security | **Difficulty:** Medium
**Room Link:** https://tryhackme.com/room/detectingwebddos

---
## What This Room Covers

Denial of Service and Distributed Denial of Service attacks against web
applications — how they work, their detection signatures, and mitigation strategies.

---
## Key Concepts Learned

**DDoS targets availability — the third pillar of the CIA triad.**
Most SOC work focuses on confidentiality (data theft) and integrity (data
modification). DDoS attacks the third pillar — making systems unavailable
to legitimate users. For Pakistan's critical infrastructure and government
web services, DDoS is a significant and politically motivated threat.

**DDoS Attack Types**

| Type | Layer | Mechanism | Example |
|---|---|---|---|
| Volumetric | L3/L4 | Flood bandwidth with traffic | UDP flood, ICMP flood |
| Protocol | L4 | Exhaust server connection state | SYN flood, Ping of Death |
| Application | L7 | Exhaust application resources | HTTP flood, Slowloris |
| Amplification | L3 | Small request, massive reflected response | DNS amplification, NTP amplification |

**Application Layer DDoS — the hardest to detect and mitigate**
L7 DDoS uses legitimate HTTP requests — the traffic looks exactly like real users.
The attack exhausts server resources (CPU, memory, database connections) by
sending valid but resource-intensive requests at high volume.

Slowloris is a classic example: it sends partial HTTP requests and keeps connections
open indefinitely, exhausting the server's connection pool without sending
large volumes of traffic. A server with 1000 connection limit can be taken down
by 1001 Slowloris connections.

**DDoS Detection Signatures in Web Logs**

```
Normal traffic pattern:
- Varied source IPs
- Varied User-Agents
- Varied requested resources
- Traffic volume following time-of-day patterns

DDoS traffic pattern:
- High volume of requests from same IP or IP range
- Identical or very similar User-Agents
- Same resource requested repeatedly
- Traffic spike inconsistent with time of day
- Unusual geographic source concentration
```

**SIEM-based DDoS detection**
```spl
index=main sourcetype=access_combined
| timechart span=1m count as requests_per_minute
| where requests_per_minute > 10000
```

Baseline the normal peak traffic volume, alert when it exceeds a multiple
of that baseline — 10x peak traffic in 1 minute is a DDoS indicator.

```spl
index=main sourcetype=access_combined
| stats count by clientip
| where count > 1000
| sort -count
```

Single IPs generating over 1000 requests — either botnet nodes or scanners.

**Rate limiting and WAF as mitigation**
Detection alone is insufficient — DDoS response requires action:
- Rate limiting: block IPs exceeding request thresholds
- Geo-blocking: block traffic from source countries with no business relationship
- CDN/WAF: absorb volumetric attacks at the edge before they reach origin servers
- ISP-level blackholing: for volumetric attacks, null-route traffic upstream

**Pakistan-specific DDoS context**
Pakistani government websites, news organizations, and financial services have
been targeted by DDoS attacks during periods of geopolitical tension.
PKCERT coordinates DDoS response at a national level — understanding detection
and mitigation is directly relevant to that mission.

---
## Hands-On Tasks

Analyzed web access logs during simulated DDoS scenarios — identified traffic
volume anomalies, classified DDoS type by signature, identified source
distribution patterns, and applied SIEM queries to detect the attack onset.

---
## How This Applies to Real SOC Work

DDoS detection requires fast action — a DDoS in progress needs to be identified
and mitigated in minutes, not hours. The combination of SIEM alerting on traffic
thresholds and established mitigation runbooks determines whether a DDoS takes
a service down for minutes or hours. As a PKCERT analyst, coordinating DDoS
response for national infrastructure makes this directly operational knowledge.

---
## Path Complete

This write-up completes the TryHackMe SOC Level 1 path documentation.

The full path covered: SOC fundamentals and workflows, cyber defence frameworks
(Pyramid of Pain, Kill Chain, MITRE ATT&CK), phishing analysis end-to-end,
network traffic analysis with Wireshark and NetworkMiner, network security
including IDS and Snort, and web security from fundamentals through attack detection.

Every concept documented here feeds directly into the hands-on detection work
in my [SIEM Detection Lab](https://github.com/Haadi-Balouch/siem-detection-lab)
and the threat intelligence analysis in my
[Threat Intel Reports](https://github.com/Haadi-Balouch/threat-intel-reports).

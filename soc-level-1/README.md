# 🔵 SOC Level 1 — Write-ups

> Complete write-ups for the TryHackMe SOC Level 1 learning path.
> This path builds the core skills of a Tier 1 SOC Analyst — from alert triage
> and SIEM usage to phishing analysis, network traffic inspection, and web attack detection.

**Path Link:** [TryHackMe SOC Level 1](https://tryhackme.com/path/outline/soclevel1)
**Status:** ✅ Complete
**Total Rooms:** 42

---

## 📊 Progress Overview

| Module | Rooms | Write-ups | Status |
|---|---|---|---|
| SOC Fundamentals | 14 | 14 | ✅ |
| Cyber Defence Frameworks | 6 | 6 | ✅ |
| Phishing | 7 | 7 | ✅ |
| Network Traffic Analysis | 5 | 5 | ✅ |
| Network Security | 6 | 6 | ✅ |
| Web Security | 4 | 4 | ✅ |

---

## 📁 Module 1 — SOC Fundamentals

Building the foundational knowledge of how a SOC operates, what tools it uses,
and how a Tier 1 analyst fits into the blue team structure.

| Room | Write-up | Key Topic |
|---|---|---|
| Junior Security Analyst Intro | [Link](./01-soc-fundamentals/junior-security-analyst-intro.md) | Day in the life of an L1 analyst |
| SOC Role in Blue Team | [Link](./01-soc-fundamentals/soc-role-in-blue-team.md) | Tier structure and career progression |
| Humans as Attack Vectors | [Link](./01-soc-fundamentals/humans-as-attack-vectors.md) | Social engineering and phishing psychology |
| Systems as Attack Vectors | [Link](./01-soc-fundamentals/systems-as-attack-vectors.md) | Vulnerabilities, misconfigurations, exploits |
| SOC L1 Alert Triage | [Link](./01-soc-fundamentals/soc-l1-alert-triage.md) | TP/FP classification and triage workflow |
| SOC L1 Alert Reporting | [Link](./01-soc-fundamentals/soc-l1-alert-reporting.md) | Incident documentation and escalation |
| SOC Workbooks and Lookups | [Link](./01-soc-fundamentals/soc-workbooks-and-lookups.md) | Playbooks and enrichment resources |
| SOC Metrics and Objectives | [Link](./01-soc-fundamentals/soc-metrics-and-objectives.md) | MTTD, MTTR, dwell time |
| Introduction to Phishing (Simulator) | [Link](./01-soc-fundamentals/intro-to-phishing-simulator.md) | First full SOC simulation scenario |
| Introduction to EDR | [Link](./01-soc-fundamentals/introduction-to-edr.md) | Endpoint detection and response fundamentals |
| Introduction to SIEM | [Link](./01-soc-fundamentals/introduction-to-siem.md) | SIEM architecture and log ingestion |
| Splunk: The Basics | [Link](./01-soc-fundamentals/splunk-the-basics.md) | SPL queries and Splunk interface |
| Elastic Stack: The Basics | [Link](./01-soc-fundamentals/elastic-stack-the-basics.md) | KQL, ECS, Kibana investigation |
| Introduction to SOAR | [Link](./01-soc-fundamentals/introduction-to-soar.md) | Automated investigation and response |

---

## 📁 Module 2 — Cyber Defence Frameworks

The strategic frameworks that structure how defenders think about threats,
adversary behavior, and detection coverage.

| Room | Write-up | Key Topic |
|---|---|---|
| Pyramid of Pain | [Link](./02-cyber-defence-frameworks/pyramid-of-pain.md) | IOC value hierarchy — hashes to TTPs |
| Cyber Kill Chain | [Link](./02-cyber-defence-frameworks/cyber-kill-chain.md) | 7-phase attack model, detection opportunities |
| Unified Kill Chain | [Link](./02-cyber-defence-frameworks/unified-kill-chain.md) | Extended model covering in-network propagation |
| MITRE ATT&CK | [Link](./02-cyber-defence-frameworks/mitre.md) | Tactics, techniques, ATT&CK Navigator |
| Summit | [Link](./02-cyber-defence-frameworks/summit.md) | Pyramid of Pain applied — adversary simulation |
| Eviction | [Link](./02-cyber-defence-frameworks/eviction.md) | Threat hunting using ATT&CK framework |

---

## 📁 Module 3 — Phishing

End-to-end phishing analysis — from understanding email anatomy through
full campaign investigation. Most operationally relevant module for the
Pakistani threat landscape given APT36's exclusive use of spearphishing.

| Room | Write-up | Key Topic |
|---|---|---|
| Phishing Analysis Fundamentals | [Link](./03-phishing/phishing-analysis-fundamentals.md) | Email headers, SPF/DKIM/DMARC |
| Phishing Emails in Action | [Link](./03-phishing/phishing-emails-in-action.md) | Real phishing sample analysis |
| Phishing Analysis Tools | [Link](./03-phishing/phishing-analysis-tools.md) | PhishTool, VirusTotal, URLScan.io |
| Phishing Prevention | [Link](./03-phishing/phishing-prevention.md) | Email authentication, gateways, user training |
| The Greenholt Phish | [Link](./03-phishing/the-greenholt-phish.md) | Full end-to-end phishing investigation challenge |
| Snapped Phish-ing Line | [Link](./03-phishing/snapped-phishing-line.md) | Full phishing campaign investigation |
| Phishing Unfolding | [Link](./03-phishing/phishing-unfolding.md) | Live phishing attack response simulation |

---

## 📁 Module 4 — Network Traffic Analysis

Packet-level network analysis using Wireshark and NetworkMiner — identifying
attack signatures, C2 patterns, and anomalous traffic in real captures.

| Room | Write-up | Key Topic |
|---|---|---|
| Network Traffic Basics | [Link](./04-network-traffic-analysis/network-traffic-basics.md) | PCAP vs NetFlow, collection methods |
| Wireshark: The Basics | [Link](./04-network-traffic-analysis/wireshark-the-basics.md) | Interface, display filters, TCP stream follow |
| Wireshark: Packet Operations | [Link](./04-network-traffic-analysis/wireshark-packet-operations.md) | Statistics, advanced filters, GeoIP |
| Wireshark: Traffic Analysis | [Link](./04-network-traffic-analysis/wireshark-traffic-analysis.md) | C2 detection, exfiltration patterns, anomalies |
| NetworkMiner | [Link](./04-network-traffic-analysis/networkminer.md) | Automated artifact extraction from PCAPs |

---

## 📁 Module 5 — Network Security

Network-based attack detection — from discovery and scanning through data
exfiltration, MITM attacks, and IDS/IPS with Snort.

| Room | Write-up | Key Topic |
|---|---|---|
| Network Security Essentials | [Link](./05-network-security/network-security-essentials.md) | Secure protocols, segmentation, defense in depth |
| Network Discovery Detection | [Link](./05-network-security/network-discovery-detection.md) | Port scan and enumeration detection |
| Data Exfiltration Detection | [Link](./05-network-security/data-exfiltration-detection.md) | DNS tunneling, HTTP exfil, volume anomalies |
| Man-in-the-Middle Detection | [Link](./05-network-security/mitm-detection.md) | ARP poisoning, SSL stripping detection |
| IDS Fundamentals | [Link](./05-network-security/ids-fundamentals.md) | Signature vs anomaly detection, NIDS vs HIDS |
| Snort | [Link](./05-network-security/snort.md) | Rule writing, modes, threshold tuning |

---

## 📁 Module 6 — Web Security

Web attack detection through log and traffic analysis — SQL injection, XSS,
directory traversal, web shells, and DDoS.

| Room | Write-up | Key Topic |
|---|---|---|
| Web Security Essentials | [Link](./06-web-security/web-security-essentials.md) | HTTP, OWASP Top 10, web server log analysis |
| Detecting Web Attacks | [Link](./06-web-security/detecting-web-attacks.md) | SQLi, XSS, enumeration signatures in logs |
| Detecting Web Shells | [Link](./06-web-security/detecting-web-shells.md) | Web shell identification, log and file monitoring |
| Detecting Web DDoS | [Link](./06-web-security/detecting-web-ddos.md) | L3/L4/L7 DDoS detection, rate-based alerting |

---

## 🔗 Related Repositories

| Repository | Relationship |
|---|---|
| [home-lab-setup](https://github.com/Haadi-Balouch/home-lab-setup) | The lab environment where concepts from these rooms are practiced hands-on |
| [security-tools](https://github.com/Haadi-Balouch/security-tools) | Deep-dive tool notes extending what was covered in THM rooms |

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
| [01 — Blue Team Introduction](#-module-1--blue-team-introduction) | 4 | 4 | ✅ |
| [02 — SOC Team Internals](#-module-2--soc-team-internals) | 5 | 5 | ✅ |
| [03 — Core SOC Solutions](#-module-3--core-soc-solutions) | 5 | 5 | ✅ |
| [04 — Cyber Defence Frameworks](#-module-4--cyber-defence-frameworks) | 6 | 6 | ✅ |
| [05 — Phishing Analysis](#-module-5--phishing-analysis) | 7 | 7 | ✅ |
| [06 — Network Traffic Analysis](#-module-6--network-traffic-analysis) | 5 | 5 | ✅ |
| [07 — Network Security](#-module-7--network-security) | 6 | 6 | ✅ |
| [08 — Web Security](#-module-8--web-security) | 4 | 4 | ✅ |

---

## 📁 Module 1 — Blue Team Introduction

Foundational understanding of the SOC environment, team structure, and the
attack surfaces that blue teamers defend against.

| Room | Write-up | Key Topic |
|---|---|---|
| Junior Security Analyst Intro | [Link](./01-blue-team-introduction/junior-security-analyst-intro.md) | Day in the life of an L1 analyst |
| SOC Role in Blue Team | [Link](./01-blue-team-introduction/soc-role-in-blue-team.md) | Tier structure and career progression |
| Humans as Attack Vectors | [Link](./01-blue-team-introduction/humans-as-attack-vectors.md) | Social engineering and phishing psychology |
| Systems as Attack Vectors | [Link](./01-blue-team-introduction/systems-as-attack-vectors.md) | Vulnerabilities, misconfigurations, exploits |

---

## 📁 Module 2 — SOC Team Internals

The internal workflows of a SOC team — how alerts are triaged, reported,
escalated, and measured.

| Room | Write-up | Key Topic |
|---|---|---|
| Introduction to Phishing (Simulator) | [Link](./02-soc-team-internals/intro-to-phishing-simulator.md) | First full SOC simulation scenario |
| SOC L1 Alert Triage | [Link](./02-soc-team-internals/soc-l1-alert-triage.md) | TP/FP classification and triage workflow |
| SOC L1 Alert Reporting | [Link](./02-soc-team-internals/soc-l1-alert-reporting.md) | Incident documentation and escalation |
| SOC Workbooks and Lookups | [Link](./02-soc-team-internals/soc-workbooks-and-lookups.md) | Playbooks and enrichment resources |
| SOC Metrics and Objectives | [Link](./02-soc-team-internals/soc-metrics-and-objectives.md) | MTTD, MTTR, dwell time |

---

## 📁 Module 3 — Core SOC Solutions

The primary tools a SOC analyst uses daily — SIEM platforms, EDR, and SOAR.

| Room | Write-up | Key Topic |
|---|---|---|
| Introduction to SIEM | [Link](./03-core-soc-solutions/introduction-to-siem.md) | SIEM architecture and log ingestion |
| Introduction to EDR | [Link](./03-core-soc-solutions/introduction-to-edr.md) | Endpoint detection and response fundamentals |
| Introduction to SOAR | [Link](./03-core-soc-solutions/introduction-to-soar.md) | Automated investigation and response |
| Splunk: The Basics | [Link](./03-core-soc-solutions/splunk-the-basics.md) | SPL queries and Splunk interface |
| Elastic Stack: The Basics | [Link](./03-core-soc-solutions/elastic-stack-the-basics.md) | KQL, ECS, Kibana investigation |

---

## 📁 Module 4 — Cyber Defence Frameworks

The strategic frameworks that structure how defenders think about adversary
behavior, threat indicators, and detection coverage.

| Room | Write-up | Key Topic |
|---|---|---|
| Pyramid of Pain | [Link](./04-cyber-defence-frameworks/pyramid-of-pain.md) | IOC value hierarchy — hashes to TTPs |
| Cyber Kill Chain | [Link](./04-cyber-defence-frameworks/cyber-kill-chain.md) | 7-phase attack model, detection opportunities |
| Unified Kill Chain | [Link](./04-cyber-defence-frameworks/unified-kill-chain.md) | Extended model covering in-network propagation |
| MITRE ATT&CK | [Link](./04-cyber-defence-frameworks/mitre.md) | Tactics, techniques, ATT&CK Navigator |
| Summit | [Link](./04-cyber-defence-frameworks/summit.md) | Pyramid of Pain applied — adversary simulation |
| Eviction | [Link](./04-cyber-defence-frameworks/eviction.md) | Threat hunting using ATT&CK framework |

---

## 📁 Module 5 — Phishing Analysis

End-to-end phishing analysis — from email anatomy through full campaign
investigation. Most operationally relevant module for the Pakistani threat
landscape given APT36's exclusive use of spearphishing.

| Room | Write-up | Key Topic |
|---|---|---|
| Phishing Analysis Fundamentals | [Link](./05-phishing-analysis/phishing-analysis-fundamentals.md) | Email headers, SPF/DKIM/DMARC |
| Phishing Emails in Action | [Link](./05-phishing-analysis/phishing-emails-in-action.md) | Real phishing sample analysis |
| Phishing Analysis Tools | [Link](./05-phishing-analysis/phishing-analysis-tools.md) | PhishTool, VirusTotal, URLScan.io |
| Phishing Prevention | [Link](./05-phishing-analysis/phishing-prevention.md) | Email authentication, gateways, user training |
| The Greenholt Phish | [Link](./05-phishing-analysis/the-greenholt-phish.md) | Full end-to-end phishing investigation challenge |
| Snapped Phish-ing Line | [Link](./05-phishing-analysis/snapped-phishing-line.md) | Full phishing campaign investigation |
| Phishing Unfolding | [Link](./05-phishing-analysis/phishing-unfolding.md) | Live phishing attack response simulation |

---

## 📁 Module 6 — Network Traffic Analysis

Packet-level network analysis using Wireshark and NetworkMiner — identifying
attack signatures, C2 patterns, and anomalous traffic in real captures.

| Room | Write-up | Key Topic |
|---|---|---|
| Network Traffic Basics | [Link](./06-network-traffic-analysis/network-traffic-basics.md) | PCAP vs NetFlow, collection methods |
| Wireshark: The Basics | [Link](./06-network-traffic-analysis/wireshark-the-basics.md) | Interface, display filters, TCP stream follow |
| Wireshark: Packet Operations | [Link](./06-network-traffic-analysis/wireshark-packet-operations.md) | Statistics, advanced filters, GeoIP |
| Wireshark: Traffic Analysis | [Link](./06-network-traffic-analysis/wireshark-traffic-analysis.md) | C2 detection, exfiltration patterns, anomalies |
| NetworkMiner | [Link](./06-network-traffic-analysis/networkminer.md) | Automated artifact extraction from PCAPs |

---

## 📁 Module 7 — Network Security

Network-based attack detection — from discovery and scanning through data
exfiltration, MITM attacks, and IDS/IPS rule writing with Snort.

| Room | Write-up | Key Topic |
|---|---|---|
| Network Security Essentials | [Link](./07-network-security/network-security-essentials.md) | Secure protocols, segmentation, defense in depth |
| Network Discovery Detection | [Link](./07-network-security/network-discovery-detection.md) | Port scan and enumeration detection |
| Data Exfiltration Detection | [Link](./07-network-security/data-exfiltration-detection.md) | DNS tunneling, HTTP exfil, volume anomalies |
| Man-in-the-Middle Detection | [Link](./07-network-security/mitm-detection.md) | ARP poisoning, SSL stripping detection |
| IDS Fundamentals | [Link](./07-network-security/ids-fundamentals.md) | Signature vs anomaly detection, NIDS vs HIDS |
| Snort | [Link](./07-network-security/snort.md) | Rule writing, modes, threshold tuning |

---

## 📁 Module 8 — Web Security

Web attack detection through log and traffic analysis — SQL injection, XSS,
directory traversal, web shells, and DDoS.

| Room | Write-up | Key Topic |
|---|---|---|
| Web Security Essentials | [Link](./08-web-security/web-security-essentials.md) | HTTP, OWASP Top 10, web server log analysis |
| Detecting Web Attacks | [Link](./08-web-security/detecting-web-attacks.md) | SQLi, XSS, enumeration signatures in logs |
| Detecting Web Shells | [Link](./08-web-security/detecting-web-shells.md) | Web shell identification, log and file monitoring |
| Detecting Web DDoS | [Link](./08-web-security/detecting-web-ddos.md) | L3/L4/L7 DDoS detection, rate-based alerting |

---

## 🔗 Related Repositories

| Repository | Relationship |
|---|---|
| [home-lab-setup](https://github.com/Haadi-Balouch/home-lab-setup) | The lab environment where concepts from these rooms are practiced hands-on |
| [security-tools](https://github.com/Haadi-Balouch/security-tools) | Deep-dive tool notes extending what was covered in THM rooms |

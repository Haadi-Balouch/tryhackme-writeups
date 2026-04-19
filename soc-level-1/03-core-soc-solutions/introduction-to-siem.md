# Introduction to SIEM

**Platform:** TryHackMe
**Path:** SOC Level 1
**Module:** SOC Fundamentals
**Difficulty:** Easy
**Room Link:** https://tryhackme.com/room/introtosiem

---

## What This Room Covers

What a SIEM is, how it works technically, and how SOC analysts use it as
the central hub of security monitoring.

---

## Key Concepts Learned

**SIEM = centralized visibility across the entire environment.**
Without a SIEM, a SOC analyst would need to log into every server, firewall,
and endpoint individually to check logs. A SIEM aggregates all of those logs
in one place, normalizes them into a searchable format, and runs detection
rules across all of them simultaneously.

**SIEM Core Functions**

| Function | What It Does |
|---|---|
| Log collection | Ingests logs from every source — servers, firewalls, endpoints, cloud |
| Normalization | Converts different log formats into consistent fields |
| Correlation | Connects related events across multiple sources |
| Alerting | Fires notifications when detection rules match |
| Dashboards | Visualizes security posture and alert trends |
| Retention | Stores historical logs for investigation and compliance |

**Log sources a SIEM typically ingests**
- Windows Event Logs (authentication, process creation, registry changes)
- Linux syslog (auth.log, system logs)
- Firewall logs (allowed/denied connections)
- DNS logs (domain lookups — often reveals C2 communication)
- Web server logs (HTTP requests — reveals web attacks)
- Email gateway logs (phishing detection)
- EDR agent events (endpoint behavior)

**Correlation is what makes SIEM powerful.**
A single failed login is noise. Five hundred failed logins from one IP in
sixty seconds is a brute force attack. A failed login followed by a successful
login from a new geographic location is a credential stuffing success.
Correlation rules connect dots across time and sources that a human reviewing
individual log files would never connect manually.

**SIEM in my home lab**
I run Splunk Free in my home lab, configured to receive syslog from Metasploitable.
This room gave me the conceptual foundation that made my Splunk setup make sense —
I was building a small-scale version of exactly the architecture this room describes.

---

## Hands-On Tasks

Explored SIEM architecture, log ingestion configuration, and the concept of
correlation rules through practical exercises.

---

## How This Applies to Real SOC Work

The SIEM is where an L1 analyst spends most of their shift. Every alert comes
through the SIEM, every investigation starts with a SIEM search. Deeply
understanding how a SIEM works — not just how to use the interface — makes
everything else faster and more effective.

---

## What I Want to Learn Next Based on This

The Splunk and Elastic rooms are the direct next step — moving from understanding
what a SIEM does conceptually to being proficient with real SIEM query languages
(SPL and KQL) in actual investigation scenarios.

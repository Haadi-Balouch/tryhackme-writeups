# Splunk: The Basics

**Platform:** TryHackMe
**Path:** SOC Level 1
**Module:** SOC Fundamentals
**Difficulty:** Easy
**Room Link:** https://tryhackme.com/room/splunk101

---

## What This Room Covers

Hands-on introduction to Splunk — navigating the interface, understanding
data ingestion, and writing basic SPL queries to search and analyze log data.

---

## Key Concepts Learned

**Splunk's interface has five main areas a SOC analyst uses:**

| Area | Purpose |
|---|---|
| Search & Reporting | Where all log searching and investigation happens |
| Dashboards | Pre-built and custom visualizations of security data |
| Alerts | Detection rules that notify when conditions are met |
| Settings | Data inputs, indexes, user management |
| Reports | Saved searches and scheduled outputs |

**The SPL (Search Processing Language) basics**

SPL reads left to right through pipes. Each command transforms the data
and passes results to the next command:

```spl
index=main sourcetype=syslog "Failed password"
| stats count by src_ip, user
| where count > 10
| sort -count
```

Reading this: find all syslog events containing "Failed password", count
them grouped by source IP and username, keep only groups with more than 10
failures, sort by count descending.

**The most important SPL concepts from this room:**
- `index=` specifies where to search
- `sourcetype=` filters by the type of log
- `| stats count by [field]` is the most used aggregation
- `| table [fields]` controls what columns display
- `| timechart count` shows event volume over time
- Time range picker controls how far back to search

**Splunk's data pipeline**
```
Data Source → Universal Forwarder → Indexer → Search Head
```
The forwarder collects logs, the indexer stores and indexes them, the
search head is the UI where analysts run queries. In my home lab Splunk
installation, all three components run on a single Kali Linux instance —
the "single instance" deployment common in small environments and home labs.

---

## Hands-On Tasks

This room was fully hands-on inside a Splunk instance. Completed exercises:
- Navigating the Splunk interface and understanding data ingestion
- Writing SPL queries to search for specific events
- Using `stats`, `table`, `sort`, and `timechart` commands
- Investigating a simulated security event using log data

---

## How This Applies to Real SOC Work

Every investigation I will ever run at PKCERT or any SOC starts with a SIEM
search. SPL proficiency directly translates to investigation speed — the
faster I can write accurate queries, the faster I can confirm or dismiss
an alert. This room built the foundation that my home lab Splunk work extends.

---

## What I Want to Learn Next Based on This

Splunk 2 (the follow-on room) covers more advanced SPL and investigation
scenarios. Beyond that, the SIEM detection lab in my home lab is where
I practice writing and testing detection rules against real attack traffic
I generate myself — the most effective way to build SPL proficiency.

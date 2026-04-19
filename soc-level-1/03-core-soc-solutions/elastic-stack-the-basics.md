# Elastic Stack: The Basics

**Platform:** TryHackMe
**Path:** SOC Level 1
**Module:** SOC Fundamentals
**Difficulty:** Easy
**Room Link:** https://tryhackme.com/room/investigatingwithelk101

---

## What This Room Covers

Hands-on introduction to the Elastic Stack (ELK) — Elasticsearch, Logstash,
and Kibana — and how SOC analysts use it for log investigation and threat detection.

---

## Key Concepts Learned

**ELK Stack Architecture**

```
Log Sources → Beats/Logstash → Elasticsearch → Kibana
(endpoints)   (collect/parse)   (store/index)   (search/visualize)
```

The architecture is conceptually identical to Splunk's pipeline but the
implementation and query language are different. Knowing both is a genuine
career advantage since organizations use both extensively.

**Kibana Query Language (KQL) vs Splunk's SPL**

| | KQL (Elastic) | SPL (Splunk) |
|---|---|---|
| Syntax style | Simpler, more intuitive | More powerful, steeper curve |
| Basic search | `event.action: "failed-login"` | `index=main "Failed password"` |
| Field filtering | `source.ip: "10.0.0.1"` | `src_ip="10.0.0.1"` |
| Aggregations | Done in Kibana UI or Lens | `\| stats count by field` |

**Elastic Common Schema (ECS)**
Elastic uses standardized field names across all log types:
- `source.ip` — source IP address
- `destination.port` — destination port
- `event.action` — what happened
- `event.outcome` — success, failure, unknown
- `process.name` — name of the process
- `user.name` — username involved

ECS makes Kibana searches more predictable — once you know the field naming
convention, you can search any log type without needing to look up field names first.

**Kibana Discover vs Dashboard**
Discover is for raw log investigation — searching, filtering, examining individual events.
Dashboards are for ongoing monitoring — visualizing patterns, alert trends, traffic volume.
An L1 analyst spends most time in Discover during active investigation.

---

## Hands-On Tasks

Investigated a simulated security incident using a pre-configured Kibana instance:
- Used KQL to filter events by IP, username, and event type
- Built a timeline of attacker activity from log data
- Identified the affected user and the scope of the compromise
- Used Kibana dashboards to visualize attack patterns

---

## How This Applies to Real SOC Work

Many organizations run Elastic instead of Splunk for cost reasons — Elastic
is open-source and free at its core. Being comfortable with both SIEM platforms
makes me employable at a wider range of organizations. The investigative
workflow is identical; only the query syntax changes.

---

## What I Want to Learn Next Based on This

Adding an ELK stack to my home lab alongside Splunk — running both against
the same attack traffic and comparing how the same event looks in each SIEM —
would build dual-platform proficiency more effectively than any room alone.

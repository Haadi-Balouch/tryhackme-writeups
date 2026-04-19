# Introduction to SOAR

**Platform:** TryHackMe
**Path:** SOC Level 1
**Module:** SOC Fundamentals
**Difficulty:** Easy
**Room Link:** https://tryhackme.com/room/introsoar

---

## What This Room Covers

Security Orchestration, Automation, and Response — how SOCs automate
repetitive triage steps to reduce analyst workload and response time.

---

## Key Concepts Learned

**SOAR automates the repetitive parts of investigation.**
Every time a phishing alert fires, an analyst runs the same lookups:
check sender reputation, check URL in VirusTotal, check if the user clicked.
SOAR platforms automate these steps the moment an alert fires, so by the
time the analyst opens the ticket, enrichment data is already there.

**The three pillars of SOAR**

| Pillar | What It Does |
|---|---|
| Orchestration | Connects different security tools so they work together automatically |
| Automation | Runs predefined investigation and response steps without human input |
| Response | Takes containment actions — blocking IPs, isolating endpoints, resetting passwords |

**SOAR workflow example — phishing alert:**
```
Alert fires in SIEM
    → SOAR automatically queries VirusTotal for all URLs in the email
    → SOAR checks sender domain age via WHOIS
    → SOAR looks up sender IP reputation
    → SOAR checks if any user in the org clicked the link (from proxy logs)
    → SOAR creates an enriched ticket with all findings pre-populated
    → Analyst reviews the enriched ticket (5 minutes instead of 45)
    → If confirmed TP: SOAR automatically blocks sender domain at email gateway
```

**SOAR is not a replacement for analysts.**
The room was clear on this: SOAR handles the mechanical, repeatable parts.
The analyst provides judgment — contextual understanding that automation
cannot replicate. An alert with unusual business context, a new attack technique
without a playbook, an ambiguous indicator — these still require human assessment.

**Popular SOAR platforms**
Palo Alto XSOAR (formerly Demisto), Splunk SOAR (formerly Phantom), IBM QRadar SOAR,
and Microsoft Sentinel (built-in SOAR capabilities).

---

## Hands-On Tasks

Explored SOAR playbook concepts and walked through automated investigation
workflows — seeing how a multi-step investigation that takes a human 30 minutes
can be reduced to seconds when properly automated.

---

## How This Applies to Real SOC Work

As an L1 analyst, SOAR is a force multiplier. It does not replace me — it
handles the repetitive enrichment steps so I can focus on the judgment-requiring
parts of triage. Understanding what SOAR can and cannot do also helps me
identify which parts of my manual workflow could eventually be automated,
which is a valuable contribution as I grow into more senior roles.

---

## What I Want to Learn Next Based on This

Understanding SOAR automation deeply requires first understanding the manual
investigation process deeply — you cannot automate what you do not understand.
The rest of the SOC Level 1 path builds that manual proficiency, after which
SOAR becomes genuinely useful rather than a black box.

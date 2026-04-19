# Junior Security Analyst Intro

**Platform:** TryHackMe
**Path:** SOC Level 1
**Module:** SOC Fundamentals
**Difficulty:** Easy
**Room Link:** https://tryhackme.com/room/jrsecanalystintro

---

## What This Room Covers

A guided walkthrough of a day in the life of a Tier 1 SOC analyst. The room
simulates the actual workflow of monitoring alerts, investigating suspicious
activity, and making triage decisions — exactly what I am training to do.

---

## Key Concepts Learned

**The SOC analyst's primary job is not to stop every attack — it is to detect and respond faster than the attacker can act.**

The room made this concrete. An analyst sits at a SIEM dashboard, reviews incoming
alerts, determines which ones are real threats versus false positives, and escalates
appropriately. It sounds straightforward until you realize the volume — a busy SOC
can generate hundreds of alerts per shift, and missing one real threat among hundreds
of false positives is genuinely dangerous.

**Triage is a skill, not just a process.**
The room introduced the idea that not all alerts are equal. A Tier 1 analyst's
job is to quickly sort alerts by likelihood and severity — is this a misconfigured
scanner triggering noise, or is this actual malicious activity? Developing fast,
accurate triage judgment is what separates a good L1 from a mediocre one.

**The SOC analyst is the first line of defense.**
Before an incident gets escalated to Tier 2 or IR teams, it passes through a
Tier 1 analyst first. The quality of that initial assessment shapes everything
that follows — poor triage means either missed threats or wasted senior analyst time.

---

## Hands-On Tasks

The room included a simulated SOC dashboard where I had to:
- Review a queue of incoming alerts
- Identify which alerts were genuine threats versus benign activity
- Make a triage decision and document the reasoning
- Escalate the correct alert to the next tier

Working through this simulation made the abstract concept of "alert triage" feel
real. The time pressure of a queue backing up while you investigate is something
no amount of reading prepares you for.

---

## How This Applies to Real SOC Work

This room is essentially a preview of the entire job. Every other room in the
SOC Level 1 path — Wireshark, Splunk, Snort, phishing analysis — is just a tool
that feeds into this core workflow: an alert fires, you investigate, you decide.

At PKCERT or any SOC in Pakistan, the day starts exactly like this room: open
the SIEM dashboard, check overnight alerts, begin triage. The specific tools and
threat actors will be different but the workflow is identical to what this room simulates.

---

## What I Want to Learn Next Based on This

Understanding the triage process conceptually is one thing. The next step is
building the technical depth to make fast, accurate triage decisions — which means
getting comfortable with SIEM queries, network traffic patterns, and threat frameworks.
That is exactly what the rest of this path builds toward.

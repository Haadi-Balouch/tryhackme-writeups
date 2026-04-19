# SOC L1 Alert Reporting

**Platform:** TryHackMe
**Path:** SOC Level 1
**Module:** SOC Fundamentals
**Difficulty:** Easy
**Room Link:** https://tryhackme.com/room/socl1alertreporting

---

## What This Room Covers

How to properly document, escalate, and communicate about SOC alerts —
specifically the written output a Tier 1 analyst produces when handing
off a confirmed threat to Tier 2 or management.

---

## Key Concepts Learned

**A good alert report is the difference between a fast response and a slow one.**
When a Tier 1 analyst escalates an incident, the Tier 2 analyst should be able
to read the report and immediately understand: what happened, on which asset,
when, what evidence exists, and what the T1 analyst already ruled out. A poor
report means the T2 analyst restarts the investigation from scratch — wasting
critical time during an active incident.

**The Anatomy of an Alert Report**

| Section | What Goes Here |
|---|---|
| Alert Summary | One-paragraph plain English description of what happened |
| Affected Assets | Hostname, IP, username, department of impacted systems/users |
| Timeline | Chronological sequence of events with timestamps |
| Evidence | Log entries, screenshots, relevant indicators |
| Analysis | Why this is classified as a TP, what attack technique was used |
| Indicators of Compromise | IPs, domains, hashes, email addresses involved |
| Recommended Action | What the analyst suggests — block IP, isolate host, reset credentials |
| Escalation Level | Is this Tier 2? IR team? Management notification? |

**Writing for a non-technical audience**
Not every report recipient is a technical analyst. Management escalations need
to be written in plain language that explains risk and business impact without
jargon. The SOC analyst who can communicate technically with peers AND clearly
with management is significantly more valuable than one who can only do the former.

**Escalation criteria**
Not every true positive needs to go to Tier 2. The room outlined escalation
thresholds — factors that push an incident up the chain:
- Confirmed data exfiltration
- Compromised privileged account
- Lateral movement detected
- Multiple hosts affected
- Critical asset (domain controller, database server) involved

**Documentation is also legal evidence**
In Pakistan's regulatory environment and internationally, SOC documentation
can become legal evidence in the event of a breach. Accurate timestamps,
factual language (no speculation without labeling it as such), and complete
evidence preservation are not just best practice — they are legally important.

---

## Hands-On Tasks

Practiced writing structured incident reports based on simulated alert scenarios.
The discipline of writing the timeline and evidence sections in particular —
being precise about what the logs actually show versus what I inferred —
was a valuable exercise in analytical writing.

---

## How This Applies to Real SOC Work

Every write-up in this GitHub repository is practicing this skill. The habit
of explaining what I did, what I found, and what it means — clearly and in
plain English — is the same habit that makes a SOC analyst's reports useful
to their team. Writing well is a technical skill in this profession.

---

## What I Want to Learn Next Based on This

The reporting skill is only as good as the investigation that precedes it.
To write a complete, accurate report I need to know how to extract the full
picture from SIEM logs, network captures, and endpoint data. That investigation
depth comes from the rest of the SOC Level 1 path.

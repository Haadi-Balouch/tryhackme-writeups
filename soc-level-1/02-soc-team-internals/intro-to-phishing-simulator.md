# Introduction to Phishing (SOC Simulator)

**Platform:** TryHackMe
**Path:** SOC Level 1
**Module:** SOC Fundamentals
**Difficulty:** Easy
**Room Link:** https://tryhackme.com/room/introtophishing

---

## What This Room Covers

An introductory hands-on scenario using the TryHackMe SOC Simulator — working
through a live phishing alert from the moment it fires to closing the ticket.
This was the first fully simulated SOC workflow in the path.

---

## Key Concepts Learned

**The SOC Simulator bridges theory and practice.**
Every concept from the triage and reporting rooms came together here in a
simulated real environment. An alert fires, a ticket opens, and I had to
work through it from start to finish as if I were actually on shift.

**Phishing is the most operationally relevant attack type in Pakistan.**
Given that APT36 and other threat actors targeting Pakistani organizations
rely almost exclusively on phishing for initial access, this scenario had
immediate real-world relevance. A phishing alert at PKCERT is not a
hypothetical — it is a daily occurrence.

**The workflow for a phishing alert**

```
Phishing alert fires (suspicious email flagged)
    ↓
Open ticket — read alert details
    ↓
Examine the email — sender, subject, headers, links, attachments
    ↓
Look up indicators — is the sender domain known malicious?
    ↓
Determine: true phishing attempt or legitimate email?
    ↓
If TP: block sender, alert affected user, check if link/attachment was clicked
    ↓
Document findings, close or escalate
```

**True Positives require immediate user action.**
If the phishing email was opened and a link clicked, the investigation
escalates immediately — the endpoint needs to be checked for malware,
credentials may be compromised, and the incident response process begins.
The phishing alert is just the starting point.

---

## Hands-On Tasks

Completed the full SOC Simulator scenario — worked an actual phishing alert
from queue to closure, making triage decisions and documenting findings in
the simulator's ticket system.

---

## How This Applies to Real SOC Work

This scenario is indistinguishable from what a first day at PKCERT would look like.
The tools and interface will be different, but the workflow, the thought process,
and the documentation requirements are identical. This room was the most
practically useful in the fundamentals module.

---

## What I Want to Learn Next Based on This

The phishing module — deep technical analysis of email headers, attachment
analysis, URL reputation checking — is the direct follow-on. The simulator
taught the workflow; the phishing module teaches the technical depth needed
to execute that workflow at a professional level.

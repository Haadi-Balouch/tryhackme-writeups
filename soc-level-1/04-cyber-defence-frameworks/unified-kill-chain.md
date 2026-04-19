# Unified Kill Chain

**Platform:** TryHackMe
**Path:** SOC Level 1
**Module:** Cyber Defence Frameworks
**Difficulty:** Easy
**Room Link:** https://tryhackme.com/room/unifiedkillchain

---

## What This Room Covers

An extended kill chain framework that improves on the original by covering
the full scope of in-network attacker activity after initial compromise.

---

## Key Concepts Learned

**Why extend the original Kill Chain?**
Lockheed Martin's original model ends at Actions on Objectives, effectively
treating initial access and final objective as nearly adjacent steps. In reality
sophisticated attackers spend weeks or months between those two points —
mapping the network, escalating privileges, moving laterally, and establishing
redundant persistence. The UKC models this reality.

**Three UKC Phases**

**Phase 1 — Initial Foothold**
Everything from reconnaissance through establishing the first persistent access.
Equivalent to the original Kill Chain phases 1–5.

**Phase 2 — Network Propagation (the gap the original model missed)**
- Pivoting — using the initial host to reach others
- Discovery — internal network mapping, service enumeration
- Privilege Escalation — local admin → domain admin
- Credential Access — password dumping, hash extraction
- Lateral Movement — moving to domain controllers, file servers, databases

This is where APTs spend most of their time. And this is where the most
detection opportunities exist — unusual internal connections, credential
access events, pass-the-hash attempts, administrative tool abuse.

**Phase 3 — Actions on Objectives**
Final payload execution: ransomware, data exfiltration, persistent backdoor
installation, or destructive wiping.

**The UKC changes how I think about incident scope.**
When an alert fires and I confirm Phase 2 activity — lateral movement, for
example — the incident is not "one compromised host." The incident is
"unknown number of compromised hosts, attacker has been in the network for
an unknown amount of time." The entire scope of the investigation changes.

---

## Hands-On Tasks

Mapped multi-phase attack scenarios to UKC phases — particularly focusing
on distinguishing Phase 1 from Phase 2 activity and understanding what
each phase's presence implies about overall incident scope.

---

## How This Applies to Real SOC Work

The UKC is my mental model for scoping incidents. A Phase 1 detection
(phishing email blocked) is a near-miss. A Phase 2 detection (lateral
movement in progress) is an active incident requiring immediate escalation.
The phase determines the urgency and scope of response.

---

## What I Want to Learn Next Based on This

MITRE ATT&CK provides the granular technique catalog that populates each
UKC phase with specific, named, detectable behaviors. The combination of
UKC (the map) and ATT&CK (the detailed terrain) gives a complete picture.

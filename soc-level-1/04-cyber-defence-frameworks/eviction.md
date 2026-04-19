# Eviction

**Platform:** TryHackMe
**Path:** SOC Level 1
**Module:** Cyber Defence Frameworks
**Difficulty:** Medium
**Room Link:** https://tryhackme.com/room/eviction

---

## What This Room Covers

A threat hunting scenario — using MITRE ATT&CK and framework knowledge to
find and evict a threat actor that is already operating inside an environment.

---

## Key Concepts Learned

**Threat hunting is proactive detection — searching for threats that alerts missed.**
This room simulated the scenario where an attacker has already achieved initial
access and is operating inside the network. No alert fired for their activity —
either their techniques evaded detection rules or rules did not exist for
their specific TTPs. Threat hunting is how these threats get found.

**The hunting methodology**
```
Start with a hypothesis — "An APT using living-off-the-land techniques
 may be present without triggering standard alerts"
    ↓
Identify the ATT&CK techniques associated with this hypothesis
    ↓
Identify what data sources would show these techniques
    ↓
Query SIEM/EDR for indicators of these techniques
    ↓
Investigate anything anomalous
    ↓
Confirm presence or absence — document findings either way
```

**Living-off-the-land (LotL) techniques**
Modern attackers increasingly avoid deploying custom malware — they abuse
legitimate system tools like PowerShell, WMI, certutil, and PsExec to
blend in with normal administrative activity. These are harder to detect
because the tools themselves are legitimate. Detection requires behavioral
context — who ran this tool, from where, doing what, at what time.

**ATT&CK as the hunting framework**
The room showed how ATT&CK technique IDs serve as hunting hypotheses.
Hunting for T1059.001 (PowerShell) means querying for anomalous PowerShell
execution patterns — encoded commands, execution from unusual parent processes,
connections to external IPs immediately after execution.

---

## Hands-On Tasks

Conducted a threat hunt through a simulated environment — using ATT&CK
technique knowledge to form hypotheses, query for relevant log evidence,
identify attacker activity, and document the findings needed to evict the threat.

---

## How This Applies to Real SOC Work

Threat hunting is typically a Tier 2 or Tier 3 function at mature SOCs, but
understanding the methodology as an L1 analyst makes me more effective at
triage — recognizing anomalous patterns that do not trigger rules but should
be escalated for hunting follow-up.

---

## What I Want to Learn Next Based on This

The phishing module shifts focus from frameworks to a specific, operationally
critical attack category — the most common initial access vector in the Pakistani
threat landscape.

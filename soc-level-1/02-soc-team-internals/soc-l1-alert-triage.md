# SOC L1 Alert Triage

**Platform:** TryHackMe
**Path:** SOC Level 1
**Module:** SOC Fundamentals
**Difficulty:** Easy
**Room Link:** https://tryhackme.com/room/socl1alerttriage

---

## What This Room Covers

A systematic approach to triaging SOC alerts — moving from "an alert fired"
to "I know what this is and what to do next" efficiently and accurately.

---

## Key Concepts Learned

**Triage felt natural to me — and this room explained why.**
Alert triage follows a logical, structured process. Given that I approach
problems methodically, the triage workflow clicked immediately. The challenge
is not understanding the process — it is executing it fast and accurately
under alert volume pressure.

**The Triage Process**

```
Alert Fires
    ↓
1. Understand the alert — what rule fired, what triggered it?
    ↓
2. Gather context — who is the affected user/asset? What is their role?
    ↓
3. Investigate the evidence — what do the logs actually show?
    ↓
4. Determine: True Positive or False Positive?
    ↓
5a. False Positive → document, close, consider tuning the rule
5b. True Positive → assess severity, escalate if needed, document
```

**True Positive vs False Positive — the core judgment**

| Classification | Meaning | Action |
|---|---|---|
| True Positive (TP) | Real threat, alert is correct | Escalate or respond based on severity |
| False Positive (FP) | Benign activity, alert fired incorrectly | Close with documentation, tune rule |
| True Negative (TN) | No threat, no alert | Nothing to do |
| False Negative (FN) | Real threat, no alert fired | Worst outcome — only found via hunting |

False negatives are the most dangerous outcome. An alert that never fires means
an attacker operating undetected. This is why threat hunting exists — proactively
searching for threats that detection rules missed.

**Context is everything in triage**
The same alert means different things depending on context. A port scan alert
from an internal IP at 2 AM on a weekend is far more suspicious than the same
alert from a known vulnerability scanner during business hours. Good triage means
asking: does this activity make sense given who, when, where, and how?

**Alert fatigue is a real operational problem**
The room addressed alert fatigue — when analysts are overwhelmed by false positive
volume, real threats get missed because genuine alerts are buried in noise.
Reducing false positives through rule tuning is part of an L1 analyst's
responsibility, not just Tier 3's job.

---

## Hands-On Tasks

Worked through simulated alert triage scenarios — reviewing alert details,
pulling log context, making true/false positive determinations, and documenting
the decision with reasoning. The simulation enforced the habit of always writing
down the reasoning, not just the conclusion.

---

## How This Applies to Real SOC Work

At PKCERT, an L1 analyst's shift starts with a queue of overnight alerts.
The ability to move through that queue methodically — without missing real
threats and without burning time on false positives — is the entire value
of the role. This room gave me the mental framework. The rest of my training
gives me the technical knowledge to apply it.

---

## What I Want to Learn Next Based on This

Triage speed comes from pattern recognition — quickly recognizing what normal
looks like so anomalies stand out immediately. That pattern recognition comes
from log analysis practice, SIEM work, and exposure to real attack traffic.
The SIEM and network analysis modules are the direct next step.

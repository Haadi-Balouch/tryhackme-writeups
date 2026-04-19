# SOC Metrics and Objectives

**Platform:** TryHackMe
**Path:** SOC Level 1
**Module:** SOC Fundamentals
**Difficulty:** Easy
**Room Link:** https://tryhackme.com/room/socmetricsandobjectives

---

## What This Room Covers

The key performance indicators that measure SOC effectiveness, and how
understanding them shapes the way analysts work.

---

## Key Concepts Learned

**Key SOC Metrics**

| Metric | What It Measures | Why It Matters |
|---|---|---|
| Mean Time to Detect (MTTD) | How long from attack start to alert firing | Lower = attacker has less time to operate undetected |
| Mean Time to Respond (MTTR) | How long from detection to containment | Lower = less damage from a confirmed incident |
| False Positive Rate | % of alerts that are not real threats | High FPR = alert fatigue, missed real threats |
| Alert Volume | Total alerts per shift/day | Tracks workload and detection rule noise |
| Escalation Rate | % of T1 alerts escalated to T2 | Indicates T1 triage quality |
| Dwell Time | How long an attacker was undetected | Critical — longer dwell time = more damage |

**Dwell time is the most important metric nobody talks about enough.**
The global average attacker dwell time — time from initial access to detection —
has historically been measured in weeks or months, not hours. Every day an
attacker is undetected they are expanding access, exfiltrating data, and
preparing for their final objective. Reducing dwell time is the single most
impactful thing a SOC can do.

**Metrics drive behavior — for better or worse.**
If a SOC measures analysts purely on tickets closed per shift, analysts are
incentivized to close tickets fast, not investigate thoroughly. Good SOC
leadership designs metrics that incentivize quality investigation, not just speed.
Understanding this as an L1 analyst means not gaming metrics — documenting
investigations completely even when it takes longer.

---

## Hands-On Tasks

Conceptual room examining metric frameworks and SOC performance measurement.

---

## How This Applies to Real SOC Work

PKCERT as a national CERT is accountable to government stakeholders who want
to see measurable improvement in Pakistan's cybersecurity posture. Metrics
like MTTD and incident response time are how that accountability is demonstrated.
As an L1 analyst, my individual performance contributes directly to these
organizational metrics.

---

## What I Want to Learn Next Based on This

Improving MTTD requires better detection rules — which means understanding
what to detect and how to write effective SIEM queries. That is the direct
technical extension of this conceptual room.

# Cyber Kill Chain

**Platform:** TryHackMe
**Path:** SOC Level 1
**Module:** Cyber Defence Frameworks
**Difficulty:** Easy
**Room Link:** https://tryhackme.com/room/cyberkillchainzmt

---

## What This Room Covers

Lockheed Martin's seven-phase model of a targeted cyber attack, and how
defenders can use it to identify and break the attack sequence early.

---

## Key Concepts Learned

**This framework clicked for me immediately.** The sequential structure
made sense — every attack follows a logical progression, and breaking any
single link stops the chain.

**The Seven Phases**

| Phase | Attacker Activity | Key Detection Point |
|---|---|---|
| Reconnaissance | OSINT, scanning, target profiling | Unusual external scanning of org infrastructure |
| Weaponization | Building malware, embedding in documents | Cannot detect — focus downstream |
| Delivery | Phishing email, malicious download, USB | Email gateway, web proxy, user reports |
| Exploitation | Payload executes on victim system | EDR, AV sandbox, email attachment detonation |
| Installation | Malware establishes persistence | Registry changes, scheduled tasks, startup entries |
| C2 | Infected host calls back to attacker | DNS queries, outbound HTTP/HTTPS to new domains |
| Actions on Objectives | Data theft, encryption, destruction | DLP alerts, large file transfers, mass encryption |

**Breaking the chain as early as possible is the goal.**
Disruption at Delivery (Phase 3) means no execution. At Exploitation (Phase 4)
means no persistence. At C2 (Phase 6) — the attacker is in but blind and unable
to operate. DNS-based C2 detection is one of the highest-return detections
in a SOC because most malware requires C2 to function at all.

**APT36 mapped to the Kill Chain**
- Recon: LinkedIn profiling of Pakistani government employees
- Weaponization: Crimson RAT packaged in themed Office documents
- Delivery: Spearphishing with Pakistan-relevant subject lines
- Exploitation: VBA macro execution on document open
- Installation: Registry run key persistence
- C2: HTTP beacon to attacker-controlled infrastructure
- Objectives: Credential harvesting, document exfiltration

Seeing this mapped out makes clear where PKCERT would most likely detect
an APT36 intrusion — at Delivery (email gateway) or C2 (DNS/proxy logs).

---

## Hands-On Tasks

Applied Kill Chain phases to real attack scenarios — classifying activity
by phase and identifying the most effective intervention point for each attack.

---

## How This Applies to Real SOC Work

When an alert fires during investigation I immediately ask: which phase is this?
That one question immediately tells me what happened before this alert (phases
already completed) and what is likely coming next (remaining phases), shaping
the entire investigation direction.

---

## What I Want to Learn Next Based on This

The Unified Kill Chain extends this model to cover in-network activity after
initial access — the phases that consume most of an APT's dwell time.

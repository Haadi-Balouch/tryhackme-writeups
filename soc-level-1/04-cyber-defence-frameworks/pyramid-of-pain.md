# Pyramid of Pain

**Platform:** TryHackMe
**Path:** SOC Level 1
**Module:** Cyber Defence Frameworks
**Difficulty:** Easy
**Room Link:** https://tryhackme.com/room/pyramidofpainax

---

## What This Room Covers

The Pyramid of Pain — a model categorizing threat indicators by how much
difficulty it causes an adversary when defenders detect and block them.

---

## Key Concepts Learned

**The Pyramid (bottom to top — least to most painful for attacker)**

| Level | Indicator Type | Attacker Cost to Evade |
|---|---|---|
| Bottom | Hash Values | Trivial — recompile binary, hash changes |
| 2nd | IP Addresses | Easy — rotate infrastructure within hours |
| 3rd | Domain Names | Annoying — takes effort and time to re-register |
| 4th | Network/Host Artifacts | Annoying — must modify tool behavior |
| 5th | Tools | Challenging — acquire or develop new tooling |
| Top | TTPs | Tough — must completely redesign the operation |

**The key insight: most SOC teams focus at the bottom.**
Hash blocking and IP blacklisting are necessary but cheap to evade. The real
detection value is at the top — detecting TTPs means detecting *how* an
attacker operates, not just *what specific files or IPs* they used today.
An attacker can change a hash in minutes. Changing their fundamental lateral
movement technique takes weeks of redesign.

**This framework directly influenced how I think about my Splunk detection rules.**
A rule that fires on a specific IP is low on the pyramid. A rule that fires
on "any process spawning a network connection immediately after a document
opens" is high on the pyramid — it detects the behavior regardless of which
malware family is used.

**APT36 application**
APT36's known IP ranges and domain IOCs are at the bottom two levels — useful
for quick blocking but rotated frequently. Their use of Office macro execution
and Crimson RAT's specific C2 communication pattern are higher up. Building
detections around macro-spawned processes and periodic C2-style HTTP beaconing
is far more durable than IP blocklists.

---

## Hands-On Tasks

Worked through the Summit challenge — progressively detecting and blocking
higher-level indicators and seeing the increasing cost imposed on the simulated
adversary at each pyramid level.

---

## How This Applies to Real SOC Work

Every detection rule I write is implicitly placed somewhere on this pyramid.
As I build my SIEM detection lab, this framework guides me to prioritize
behavioral, TTP-based detections over simple IOC matching wherever possible.

---

## What I Want to Learn Next Based on This

MITRE ATT&CK is the comprehensive catalog of TTPs at the top of the pyramid.
Learning the ATT&CK framework in the next room gives me the vocabulary to
describe and build detections at the highest, most impactful level.

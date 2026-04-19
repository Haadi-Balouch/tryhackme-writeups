# Summit

**Platform:** TryHackMe
**Path:** SOC Level 1
**Module:** Cyber Defence Frameworks
**Difficulty:** Medium
**Room Link:** https://tryhackme.com/room/summit

---

## What This Room Covers

A practical challenge applying the Pyramid of Pain — progressively detecting
and blocking higher-level adversary indicators until the attacker gives up.

---

## Key Concepts Learned

**The Pyramid of Pain becomes real when you apply it under pressure.**
Reading about the pyramid is one thing. Working through a scenario where
each blocked indicator forces the adversary to adapt — and seeing exactly
how quickly they circumvent low-level blocks versus how costly high-level
blocks are — makes the framework stick in a way that reading cannot.

**The escalation pattern**

Starting at the bottom:
- Block a hash → attacker recompiles binary in minutes, back to normal
- Block an IP → attacker rotates to new infrastructure within the hour
- Block a domain → takes longer, more disruption
- Block network artifacts (specific URL patterns, user agents) → forces tool modification
- Block the tool entirely → attacker must acquire or develop new tooling
- Detect the TTP (how they move, how they establish C2) → forces fundamental redesign

**The goal is not to stop every attack — it is to make the attacker's operation economically unsustainable.**
If defending against you costs the attacker more resources than the target is worth,
they will move on. This is the strategic framing behind the Pyramid — raise the
cost at every level.

**Detection engineering implication**
The summit scenario reinforced that a layered detection strategy — blocking at
every pyramid level simultaneously — is more effective than focusing entirely
on one level. Hash blocking catches known malware. TTP detection catches novel
variants. Both together leave the attacker with no easy path forward.

---

## Hands-On Tasks

Worked through the full adversary simulation — applied detections at each
pyramid level and observed attacker adaptation behavior at each stage until
the simulated adversary ceased operations.

---

## How This Applies to Real SOC Work

This scenario is essentially a simplified purple team exercise — where the
defender iteratively improves detection coverage based on observed attacker
behavior. Real purple team exercises at mature SOCs work exactly this way.
Understanding the framework behind it means I can contribute meaningfully
to detection improvement discussions even as a junior analyst.

---

## What I Want to Learn Next Based on This

Eviction applies similar concepts to a real threat hunting scenario — using
framework knowledge to proactively find an adversary that is already operating
inside the environment.

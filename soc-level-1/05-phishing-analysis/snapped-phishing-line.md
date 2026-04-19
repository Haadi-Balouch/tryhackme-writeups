# Snapped Phish-ing Line

**Platform:** TryHackMe
**Path:** SOC Level 1
**Module:** Phishing
**Difficulty:** Medium
**Room Link:** https://tryhackme.com/room/snappedphishingline

---

## What This Room Covers

A full phishing campaign investigation — analyzing multiple related phishing
emails and infrastructure to expose and document a coordinated attack.

---

## Key Concepts Learned

**Single email analysis vs campaign analysis**
Investigating one phishing email is an isolated event. Investigating a campaign
means connecting multiple emails that share infrastructure, techniques, or
targets — understanding the scope and intent of a coordinated attacker operation.

**Campaign indicators — how multiple phishing emails are linked**
- Shared sending infrastructure (same IP, same hosting provider)
- Shared URL patterns (same domain, same URL path structure)
- Same attachment with different filenames (same hash)
- Same email template with minor variations
- Targeting pattern (all victims in same department or organization)

**Infrastructure pivoting**
One URL found in one phishing email can be used to find more. If the URL
is hosted at a specific IP, checking what else is hosted at that IP often
reveals other phishing pages. If the domain was registered by a specific
registrar account, checking that account may reveal related domains.
This is how campaign scope gets mapped from a single initial indicator.

**The intelligence value of a campaign investigation**
Documenting a complete phishing campaign produces threat intelligence — the
infrastructure, TTPs, and targeting pattern of a specific threat actor.
For PKCERT, a campaign targeting Pakistani organizations would be prioritized
for national intelligence sharing.

**Connecting this to APT36**
APT36 runs phishing campaigns, not one-off emails. Their campaigns have
consistent infrastructure patterns — registered domains that follow naming
conventions, hosting providers they prefer, document templates they reuse.
Campaign analysis is how their infrastructure gets mapped and blocked
proactively before each new email lands in an inbox.

---

## Hands-On Tasks

Investigated a multi-email phishing campaign — analyzed each email, connected
shared infrastructure, pivoted from initial IOCs to related infrastructure,
documented the full campaign scope, and extracted a comprehensive IOC set.

---

## How This Applies to Real SOC Work

Campaign investigation is where individual phishing triage becomes threat
intelligence. A single blocked phishing email is a closed ticket. A documented
campaign with mapped infrastructure is an intelligence product that benefits
every other organization facing the same threat actor.

---

## What I Want to Learn Next Based on This

Phishing Unfolding simulates a live phishing attack as it unfolds in real time —
the highest-stakes phishing scenario in the path.

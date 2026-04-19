# Phishing Prevention

**Platform:** TryHackMe
**Path:** SOC Level 1
**Module:** Phishing
**Difficulty:** Easy
**Room Link:** https://tryhackme.com/room/phishingemails4gkxh

---

## What This Room Covers

The technical and procedural controls organizations deploy to reduce the
volume and impact of phishing attacks.

---

## Key Concepts Learned

**Prevention is layered — no single control stops all phishing.**

**Layer 1 — Email Authentication (stops spoofing)**

| Protocol | What It Does |
|---|---|
| SPF | Lists authorized IP addresses that can send email for a domain |
| DKIM | Cryptographically signs emails to verify they were not modified |
| DMARC | Policy that tells receiving servers what to do with SPF/DKIM failures |

Without all three properly configured, an attacker can send emails that
appear to come from your domain. DMARC with a reject policy is the complete
solution. Many Pakistani organizations have incomplete email authentication
deployment — a significant gap that APT36 exploits.

**Layer 2 — Email Gateway Filtering**
Spam filters, attachment sandboxing, URL rewriting, and malicious content
scanning before email reaches the inbox. Modern email security platforms
(Proofpoint, Mimecast, Microsoft Defender for Office 365) detonate
attachments in a sandbox and replace URLs with safe-link wrappers.

**Layer 3 — Browser and Endpoint Controls**
Web filtering that blocks known malicious URLs, even if the phishing email
is delivered. Endpoint protection that catches malware execution if the
attachment is opened.

**Layer 4 — User Awareness Training**
The only control that addresses the human element directly. Simulated
phishing campaigns that train users to recognize and report suspicious emails.
Combined with a clear, easy reporting process, user awareness training
converts the human attack surface from a vulnerability into a detection sensor.

**Layer 5 — SOC Detection and Response**
Even with all preventive layers, some phishing emails will reach users.
The SOC's role is to detect when a phishing email was clicked, contain the
resulting compromise quickly, and use each incident to improve preventive controls.

**The defender's mindset on phishing prevention**
Perfect prevention is impossible — the goal is making the attacker's job
expensive enough that most campaigns fail or are detected before causing
significant damage. Multiple layers ensure that evading one control does not
mean evading all of them.

---

## Hands-On Tasks

Examined email authentication configuration, tested DMARC policies, and
reviewed email security gateway capabilities and configuration best practices.

---

## How This Applies to Real SOC Work

As a PKCERT analyst, phishing prevention recommendations are part of the
advisory function — helping Pakistani organizations improve their email
security posture. Understanding what good email security looks like means
I can identify gaps when reviewing an organization's configuration.

---

## What I Want to Learn Next Based on This

The Greenholt Phish and Snapped Phish-ing Line rooms apply everything from
this module to full investigation challenges — analyzing real phishing campaigns
from initial email through full IOC extraction.

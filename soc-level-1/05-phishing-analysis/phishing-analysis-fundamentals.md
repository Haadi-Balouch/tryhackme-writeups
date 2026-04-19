# Phishing Analysis Fundamentals

**Platform:** TryHackMe
**Path:** SOC Level 1
**Module:** Phishing
**Difficulty:** Easy
**Room Link:** https://tryhackme.com/room/phishingemails1tryoe

---

## What This Room Covers

The anatomy of an email — every component from headers to body to attachments —
and how each component provides forensic evidence during phishing investigation.

---

## Key Concepts Learned

**Email headers were overwhelming at first — then the structure clicked.**
An email header looks like a wall of unreadable text until you understand
that it is a chronological log of every server the email passed through,
read bottom to top. Once that structure clicked, headers became one of my
most valuable investigation sources.

**Key Email Header Fields for Phishing Analysis**

| Header Field | What It Shows | Why It Matters |
|---|---|---|
| `From:` | Sender display name and address | Can be spoofed — never trust at face value |
| `Reply-To:` | Where replies go | Mismatch with From = immediate red flag |
| `Return-Path:` | Bounce address | Often reveals true sender infrastructure |
| `Received:` | Servers the email transited | Shows the email's actual origin path |
| `X-Originating-IP:` | IP that submitted the email | The actual sending server IP |
| `Message-ID:` | Unique email identifier | Format can reveal sending platform |
| `DKIM-Signature:` | Cryptographic authentication | Failed DKIM = email was modified in transit |
| `SPF:` | Sender Policy Framework result | Fail = sender not authorized to use that domain |
| `DMARC:` | Combined SPF+DKIM policy | Fail = high suspicion of spoofing |

**SPF, DKIM, DMARC — the email authentication trio**
These three mechanisms together are what organizations use to prevent email spoofing.
A legitimate email from a well-configured domain passes all three. A phishing
email impersonating that domain will typically fail one or more.

**The email body and attachments**
Beyond headers, phishing analysis examines:
- URLs — are they obfuscated? Do they redirect? What domain are they on?
- Attachments — what file type? Does the name match the extension?
- Content — urgency language, authority impersonation, unusual requests

**Pakistan-specific phishing lures**
APT36's phishing emails targeting Pakistani organizations use highly specific
lures: government job postings, scholarship notices from Pakistani universities,
defence ministry documents, and India-Pakistan geopolitical content designed
to appear credible to Pakistani recipients. The technical analysis process
is identical to generic phishing — the social engineering context is what
makes these particularly effective.

---

## Hands-On Tasks

Analyzed real email samples — examining headers using an email header analyzer,
identifying SPF/DKIM/DMARC results, locating originating IP addresses, and
assessing body content for phishing indicators.

---

## How This Applies to Real SOC Work

Phishing is the most common initial access method targeting Pakistani organizations.
As a PKCERT analyst, a large portion of the alert queue will be phishing-related.
The ability to analyze an email header quickly and accurately — extracting the
originating IP, checking authentication results, identifying spoofed domains —
is a core daily skill.

---

## What I Want to Learn Next Based on This

Phishing Emails in Action takes this theoretical analysis and applies it to
real phishing email samples — seeing exactly what different types of phishing
attempts look like in practice.

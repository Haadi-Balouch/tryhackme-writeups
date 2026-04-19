# The Greenholt Phish

**Platform:** TryHackMe
**Path:** SOC Level 1
**Module:** Phishing
**Difficulty:** Easy
**Room Link:** https://tryhackme.com/room/phishingemails5fgjlzxc

---

## What This Room Covers

A complete, end-to-end phishing investigation challenge — analyzing a real
malicious email from header examination through full IOC extraction using all
tools and techniques from the phishing module.

---

## Key Concepts Learned

**This room is where the phishing module becomes real.**
The previous rooms taught components in isolation — headers here, tools there.
The Greenholt Phish required applying all of them simultaneously, in sequence,
under the context of "what actually happened and what do I report?"

**The complete phishing investigation workflow in practice**

Starting from the raw email:
1. Read the email — what is the social engineering lure? What does it want the recipient to do?
2. Examine the From/Reply-To mismatch — is the reply going somewhere different than the sender?
3. Parse headers — where did this email actually originate? Does the originating IP match the claimed sender?
4. Check SPF/DKIM/DMARC results — did this email pass authentication?
5. Extract all URLs — check each in URLScan.io and VirusTotal
6. Extract any attachments — check hashes in VirusTotal, sandbox if needed
7. Check domain age — when was the sending domain registered?
8. Compile all IOCs — IPs, domains, URLs, file hashes
9. Write findings — true positive phishing campaign, summary of evidence, recommended actions

**What made this email clearly malicious**
The investigation revealed: Reply-To mismatch with the From address,
recently registered sending domain, URL pointing to a credential harvesting
page, and SPF failure indicating the sending server was not authorized for
that domain. Any one of these would be suspicious. All together they confirm
a phishing attempt with high confidence.

**IOC extraction — what to document**
- Sending IP address
- Sending domain and registration date
- Reply-To address
- Malicious URL(s)
- Landing page domain
- File attachment hash (if applicable)
- SPF/DKIM/DMARC status

---

## Hands-On Tasks

Completed the full Greenholt Phish investigation — analyzed all email components,
used PhishTool, VirusTotal, and URLScan.io, extracted all IOCs, and answered
investigation questions demonstrating complete phishing analysis capability.

---

## How This Applies to Real SOC Work

This room format — a complete investigation challenge with specific questions
to answer — is the closest THM gets to simulating a real phishing ticket workflow.
The discipline of working methodically, documenting each finding, and extracting
all IOCs rather than stopping at the first red flag is exactly what professional
phishing analysis requires.

---

## What I Want to Learn Next Based on This

Snapped Phish-ing Line escalates further — a full phishing campaign investigation
rather than a single email, requiring correlation across multiple related emails
and infrastructure.

# Phishing Emails in Action

**Platform:** TryHackMe
**Path:** SOC Level 1
**Module:** Phishing
**Difficulty:** Easy
**Room Link:** https://tryhackme.com/room/phishingemails2rytmuv

---

## What This Room Covers

Examining actual phishing email samples — identifying the specific indicators
that distinguish malicious emails from legitimate ones across different phishing campaign types.

---

## Key Concepts Learned

**Different phishing campaigns use different techniques — but share common indicators.**

**Phishing Campaign Types Examined**

| Type | Primary Technique | Key Indicator |
|---|---|---|
| Credential harvesting | Fake login page link | URL domain mismatch, recent domain registration |
| Malware delivery | Malicious attachment | Unusual file type, macro-enabled Office doc |
| BEC (Business Email Compromise) | Impersonated executive | Reply-To mismatch, wire transfer request |
| Spearphishing | Personalized content | Victim name/role included, relevant lure |
| Callback phishing | Phone number instead of link | Prompts victim to call a fake support number |

**The URL is the most critical analysis point in most phishing emails.**
A legitimate-looking email can be completely invalidated by a single
URL analysis. Key URL red flags:
- Domain registered in the last 30 days
- Typosquat of a legitimate domain (paypa1.com, micros0ft.com)
- URL shortener hiding the destination
- Legitimate domain as a subdomain (login.paypal.com.evil-site.com — the real domain is evil-site.com)
- URL contains the target company name but is not the real domain

**Attachment red flags**
- Office documents (.doc, .xls) from unexpected senders — macro risk
- Password-protected ZIPs — designed to bypass email scanning
- `.exe` or `.js` files — direct execution payloads
- PDF with embedded links — common credential harvest vector

**The urgency pattern**
Nearly every phishing email uses urgency: "Your account will be suspended,"
"Immediate action required," "Security alert." This is deliberate — urgency
triggers emotional response and bypasses careful evaluation. Recognizing this
pattern immediately makes analysis faster.

---

## Hands-On Tasks

Analyzed multiple real phishing email samples — examined headers, extracted and
checked URLs, identified attachment types, classified the phishing technique used,
and made a triage determination for each sample.

---

## How This Applies to Real SOC Work

This room built the pattern recognition that makes phishing triage fast. After
analyzing enough phishing samples, the indicators become immediately obvious —
the mismatched Reply-To, the recently registered domain, the urgency language.
That fast pattern recognition is what allows an L1 analyst to work through a
large phishing alert queue efficiently.

---

## What I Want to Learn Next Based on This

Phishing Analysis Tools covers the specific tools used to automate parts of this
analysis — URL reputation checking, header parsing, attachment sandboxing.

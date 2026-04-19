# Phishing Analysis Tools

**Platform:** TryHackMe
**Path:** SOC Level 1
**Module:** Phishing
**Difficulty:** Easy
**Room Link:** https://tryhackme.com/room/phishingemails3nns

---

## What This Room Covers

The specific tools SOC analysts use to investigate phishing emails — from
header analysis to URL reputation to attachment sandboxing.

---

## Key Concepts Learned

**Phishing analysis tools reduce manual investigation time significantly.**
Manually analyzing every URL and header field is slow. These tools automate
the most time-consuming lookups and provide enriched context within seconds.

**Core Phishing Analysis Tools**

| Tool | Purpose | What It Gives You |
|---|---|---|
| PhishTool | Automated phishing email analysis | Full header analysis, URL extraction, IOC summary |
| VirusTotal | File and URL reputation | Community detection rate, sandboxed behavior |
| URLScan.io | URL analysis and screenshot | What the URL renders as, redirects, domain info |
| MXToolbox | Email header and DNS analysis | SPF/DKIM/DMARC results, mail server info |
| AnyRun | Interactive malware sandbox | Live execution of attachments, network traffic |
| Hybrid Analysis | Static and dynamic file analysis | Deep malware behavioral analysis |
| WHOIS | Domain registration lookup | Domain age, registrar, registration country |
| Talos Intelligence | Cisco's threat intelligence | IP/domain reputation, email reputation |

**The phishing triage workflow with tools**

```
Phishing alert fires
    ↓
Open email in PhishTool or extract headers manually
    ↓
Check SPF/DKIM/DMARC → fail = suspicious
    ↓
Extract originating IP → check in VirusTotal/Talos
    ↓
Extract all URLs → check each in URLScan.io
    ↓
If attachment present → submit to AnyRun or Hybrid Analysis
    ↓
Check domain age → WHOIS (newly registered = suspicious)
    ↓
Compile findings → True Positive or False Positive determination
```

**VirusTotal nuances**
A VirusTotal result of 0/72 does not mean a file is safe — it means no known
AV vendor has a signature for it yet. New malware always starts at 0/72. Context
matters: a 0/72 PDF from a known, legitimate sender is probably fine. A 0/72
macro-enabled document from an unknown sender received with an urgent subject
line warrants sandbox analysis regardless of the VT result.

---

## Hands-On Tasks

Used PhishTool, VirusTotal, and URLScan.io on real phishing email samples —
extracted IOCs, checked reputation, assessed attachment risk, and made triage
determinations using the tool output.

---

## How This Applies to Real SOC Work

These tools are part of the standard phishing triage workflow at virtually
every SOC. Knowing how to use them efficiently — what to look for, what a
result means, and when to dig deeper — directly translates to faster, higher
quality phishing alert handling.

---

## What I Want to Learn Next Based on This

Phishing Prevention covers the defensive controls that reduce phishing volume
and impact — email authentication, filtering, and user awareness programs.

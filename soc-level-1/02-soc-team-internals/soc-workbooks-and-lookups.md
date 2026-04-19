# SOC Workbooks and Lookups

**Platform:** TryHackMe
**Path:** SOC Level 1
**Module:** SOC Fundamentals
**Difficulty:** Easy
**Room Link:** https://tryhackme.com/room/socworkbooksandlookups

---

## What This Room Covers

The structured resources SOC teams use to standardize and speed up alert
triage — workbooks, playbooks, and lookup tables that remove guesswork
from the investigation process.

---

## Key Concepts Learned

**Workbooks are the SOC's standard operating procedures.**
A workbook (also called a playbook) is a step-by-step guide for investigating
a specific alert type. When a phishing alert fires, the workbook tells the
analyst exactly what to check, in what order, and what constitutes a true
versus false positive for that specific alert type.

Without workbooks, every analyst makes different judgment calls. With workbooks,
the team is consistent — the same alert gets the same quality of investigation
regardless of who is on shift.

**Common SOC Workbook Types**

| Workbook | Covers |
|---|---|
| Phishing Triage | Steps to analyze a suspicious email alert |
| Malware Alert | Steps to investigate a malware detection on an endpoint |
| Brute Force | Steps to investigate repeated authentication failures |
| Data Exfiltration | Steps to investigate large outbound data transfers |
| Lateral Movement | Steps to investigate unusual internal network connections |

**Lookup Tables — instant context during investigation**
Lookup tables map raw data to meaningful context. Examples:

- IP reputation lookup — is this IP known malicious?
- Domain age lookup — was this domain registered recently?
- User lookup — what department is this user in, what is their role?
- Asset lookup — what is this hostname, what data does it hold?
- Hash lookup — has this file hash been seen before, is it known malware?

The difference between a 5-minute triage and a 45-minute triage is often
whether the analyst has good lookup resources immediately available.

**Automation potential**
The room introduced the concept that workbook steps can be automated — a
SOAR platform can automatically run the first several lookup steps the moment
an alert fires, giving the analyst enriched context before they even open the ticket.
This connects directly to the SOAR room later in the path.

---

## Hands-On Tasks

Practiced using workbook-style checklists to work through alert scenarios
systematically, and used lookup resources to enrich alert data with context.

---

## How This Applies to Real SOC Work

At PKCERT, standardized workbooks are what allow a team to handle high alert
volumes consistently. As an L1 analyst I would follow these workbooks precisely,
and over time contribute to improving them based on patterns I notice in
recurring false positives or missed detections.

---

## What I Want to Learn Next Based on This

Workbooks are only as good as the analyst's ability to execute them. Understanding
the tools referenced in each workbook step — SIEM queries, threat intel lookups,
network analysis — is what makes the workbook actionable rather than just a checklist.

# Phishing Unfolding

**Platform:** TryHackMe
**Path:** SOC Level 1
**Module:** Phishing
**Difficulty:** Medium
**Room Link:** https://tryhackme.com/room/phishingunfolding

---

## What This Room Covers

A simulated live phishing attack as it unfolds within a corporate network —
from the initial email delivery through user interaction, credential theft,
and the SOC response in real time.

---

## Key Concepts Learned

**Phishing response is time-critical.**
Once a user clicks a phishing link and submits credentials, the attacker has
working credentials immediately. The window between credential submission and
attacker use is often minutes — sometimes seconds for automated credential
stuffing. Speed of detection and response is everything.

**The incident timeline in a live phishing attack**

```
T+0:00  Phishing email delivered to user inbox
T+X:XX  User opens email
T+X:XX  User clicks malicious link
T+X:XX  User submits credentials on fake login page (BREACH MOMENT)
T+X:XX  Attacker receives stolen credentials
T+X:XX  Attacker attempts login with stolen credentials
T+X:XX  SOC detects anomalous login (new location, new device)
T+X:XX  SOC triage begins
T+X:XX  Account suspended, password reset forced
T+X:XX  Scope assessment — what did the attacker access?
```

**The SOC's role during a live phishing incident**
- Identify affected user(s) immediately
- Determine if credentials were submitted (check proxy logs for phishing URL)
- Check for successful logins from the attacker's IP
- Suspend affected accounts immediately if compromise confirmed
- Force password reset for affected user and anyone who may share credentials
- Scope the access — what did the attacker do with the credentials in the window?
- Collect and preserve all evidence
- Notify the affected user and their manager per escalation procedures

**Indicators that credentials were submitted**
In proxy/web gateway logs: a POST request to the phishing URL from the victim's
workstation IP. This is the confirmation that credential theft occurred —
a GET request (loading the page) is exposure, a POST request (form submission)
is confirmed compromise.

---

## Hands-On Tasks

Worked through a live phishing scenario — monitored as the attack progressed,
identified the moment of credential compromise, responded in the correct
sequence, and documented the full incident timeline.

---

## How This Applies to Real SOC Work

This room simulates the highest-pressure phishing scenario — an active, ongoing
compromise. The discipline of working the correct sequence (contain first,
then investigate scope) rather than investigating while the attacker is still
active is critical. Reversing the order means the attacker continues to operate
while you investigate what they already did.

---

## What I Want to Learn Next Based on This

The network traffic analysis module shifts focus to a different but equally
critical detection area — identifying malicious activity in network packets
and flows, including C2 communication that follows credential-based initial access.

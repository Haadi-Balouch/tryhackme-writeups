# Humans as Attack Vectors

**Platform:** TryHackMe
**Path:** SOC Level 1
**Module:** SOC Fundamentals
**Difficulty:** Easy
**Room Link:** https://tryhackme.com/room/humansasattackvectors

---

## What This Room Covers

Why people — not systems — are the most frequently exploited attack surface,
how social engineering works, and what the SOC's role is in detecting and
responding to human-targeted attacks.

---

## Key Concepts Learned

**The human is the weakest link — and the hardest to patch.**
Firewalls, IDS rules, and SIEM detections can be tuned and updated. Human
behavior cannot be patched with a software update. This is why social engineering
remains the most common initial access technique in real-world attacks. APT36,
the threat group most relevant to Pakistan, uses spearphishing almost exclusively
as its entry point — targeting people, not systems.

**Social Engineering Attack Types**

| Attack Type | How It Works |
|---|---|
| Phishing | Mass email campaign impersonating trusted entities |
| Spearphishing | Targeted phishing — personalized to the specific victim |
| Smishing | Phishing via SMS |
| Vishing | Phishing via voice call |
| Pretexting | Creating a false scenario to extract information |
| Baiting | Leaving malware-infected USB drives in physical locations |

**Why Pakistan is particularly vulnerable to phishing**
The room's content connected directly to the Pakistani threat landscape in my mind.
APT36 (Transparent Tribe) runs highly targeted spearphishing campaigns against
Pakistani government employees, military personnel, and university students —
using fake government documents, scholarship notices, and job offers as lures.
Understanding how humans are manipulated is not abstract here — it is a daily
operational reality for Pakistani SOC teams.

**The SOC's role against human-targeted attacks**
The SOC cannot prevent a user from clicking a phishing link. But it can:
- Detect the malicious attachment executing after the click
- Detect the C2 callback that follows initial access
- Detect lateral movement once the attacker is inside
- Contain the infection before it spreads

This is why detecting the *consequences* of human error matters more than
trying to prevent the human error itself.

---

## Hands-On Tasks

Conceptual room exploring social engineering scenarios and how the SOC
monitors and responds to attacks that begin with human interaction.

---

## How This Applies to Real SOC Work

Given that phishing is the most common initial access vector in Pakistan-targeted
attacks, this room is directly relevant to daily work at PKCERT. Every phishing
email that lands in a Pakistani government inbox is a potential APT36 intrusion
attempt. Understanding why humans click — urgency, authority, familiarity —
makes me a better analyst when reviewing phishing alerts, because I understand
the attacker's psychology alongside the technical indicators.

---

## What I Want to Learn Next Based on This

The natural follow-on is the phishing module — specifically learning to analyze
phishing emails technically (headers, attachments, URLs) and how to use tools
like PhishTool and VirusTotal to process phishing alerts efficiently.

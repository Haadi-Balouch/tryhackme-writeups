# MITRE ATT&CK

**Platform:** TryHackMe
**Path:** SOC Level 1
**Module:** Cyber Defence Frameworks
**Difficulty:** Easy
**Room Link:** https://tryhackme.com/room/mitre

---

## What This Room Covers

The MITRE ATT&CK framework — the industry-standard knowledge base of adversary
tactics, techniques, and procedures used for detection engineering, threat hunting,
and threat intelligence.

---

## Key Concepts Learned

**ATT&CK felt very large at first — and it is.**
The framework contains hundreds of techniques across 14 tactics. The key
insight that made it manageable: you do not need to know all of them. You need
to know the ones relevant to your threat landscape and use the framework as a
reference, not memorize it.

**The ATT&CK Structure**

```
Tactics (14 — the WHY)
    └── Techniques (HOW the tactic is achieved)
            └── Sub-techniques (specific implementation details)
```

**The 14 Tactics**

| Tactic | What the Attacker is Doing |
|---|---|
| Reconnaissance | Gathering target information |
| Resource Development | Building infrastructure and tools |
| Initial Access | Getting into the environment |
| Execution | Running malicious code |
| Persistence | Maintaining access after reboots |
| Privilege Escalation | Gaining higher permissions |
| Defense Evasion | Avoiding detection |
| Credential Access | Stealing passwords and hashes |
| Discovery | Mapping the internal environment |
| Lateral Movement | Moving to other hosts |
| Collection | Gathering target data |
| Command & Control | Communicating with the implant |
| Exfiltration | Stealing data out of the environment |
| Impact | Disrupting, destroying, or ransoming |

**How I use ATT&CK in my threat intel reports**
In my `threat-intel-reports` GitHub repo, every APT report includes a MITRE
ATT&CK TTP mapping table. APT36's profile maps to: T1566.001 (Spearphishing
Attachment), T1059.005 (VBA Macros), T1547.001 (Registry Run Key), T1071.001
(Web Protocols for C2), T1041 (Exfiltration Over C2). These technique IDs are
the universal language for describing attacker behavior.

**ATT&CK Navigator**
The ATT&CK Navigator is a free web tool for visualizing which techniques an
adversary uses, which techniques an organization detects, and where coverage
gaps exist. Building a Navigator layer for APT36 — coloring in their known
techniques — immediately shows PKCERT which detections are most critical.

**ATT&CK for detection engineering**
Each ATT&CK technique page includes data sources — what logs or telemetry
would show this technique being used. Technique T1110 (Brute Force) lists
authentication logs as a data source. This tells me exactly what to query
in Splunk to detect brute force, and the ATT&CK ID becomes the tag I attach
to the detection rule.

---

## Hands-On Tasks

Explored the ATT&CK website, navigated techniques for specific tactics, used
the ATT&CK Navigator to build threat actor profiles, and applied the framework
to analyze attack scenarios by mapping activity to specific technique IDs.

---

## How This Applies to Real SOC Work

ATT&CK is the shared vocabulary of the security industry. When I write a detection
rule in Splunk and tag it `T1110 - Brute Force`, every analyst on the team
immediately understands what it detects without reading the rule. When PKCERT
receives threat intelligence about a new attack campaign, mapping it to ATT&CK
techniques immediately tells the team which existing detections apply and where
new ones are needed.

---

## What I Want to Learn Next Based on This

The Summit and Eviction rooms apply these frameworks to real adversary simulation
scenarios — testing whether detection coverage is sufficient to catch an attacker
moving through the ATT&CK matrix.

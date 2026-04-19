# Systems as Attack Vectors

**Platform:** TryHackMe
**Path:** SOC Level 1
**Module:** SOC Fundamentals
**Difficulty:** Easy
**Room Link:** https://tryhackme.com/room/systemsasattackvectors

---

## What This Room Covers

How attackers exploit vulnerable and misconfigured systems — the technical
attack surface alongside the human one — and what defenders can do to reduce it.

---

## Key Concepts Learned

**Vulnerability vs Misconfiguration — two different problems**

| Type | What It Is | Example |
|---|---|---|
| Vulnerability | A flaw in software or hardware | CVE-2021-44228 (Log4Shell) |
| Misconfiguration | Correct software, wrong settings | SSH running as root with default password |
| Unpatched system | Known vulnerability, no fix applied | Eternal Blue (MS17-010) years after patch |

Both are equally dangerous. Metasploitable 2 — which I run in my home lab —
is a perfect example of both: intentionally vulnerable software versions AND
default credentials across every service. In real environments, misconfigurations
are often more common than unpatched vulnerabilities because they are harder to
detect systematically.

**The attack surface is everything that is reachable**
The room reinforced that the attack surface includes every open port, every
running service, every exposed API, every user account, and every piece of
software with a known CVE. Reducing attack surface is the foundation of defense.
The Nmap scan output I generated against Metasploitable — 10+ open services —
is a perfect illustration of an excessive attack surface.

**Common system attack techniques**

| Technique | What Happens |
|---|---|
| Exploitation | Attacker uses a known CVE to gain access |
| Brute force | Repeated authentication attempts against a service |
| Default credentials | Login using unchanged factory credentials |
| Service misconfiguration | Abuse of a service running with excessive permissions |
| Supply chain attack | Compromise via a trusted third-party dependency |

**Patch management is a SOC concern**
A SOC analyst needs to know about recent CVEs affecting the organization's
software stack. When a critical CVE drops — like Log4Shell — the SOC's job is
to search SIEM logs for exploitation attempts against affected systems before
a patch can be deployed. This is threat hunting triggered by external intelligence.

---

## Hands-On Tasks

Conceptual room examining system attack scenarios and defense strategies.
The concepts here connect directly to hands-on work in my home lab — the
vsftpd backdoor and Samba exploits I ran against Metasploitable are real
examples of the system-level attacks this room describes.

---

## How This Applies to Real SOC Work

Pakistani organizations — government, finance, telecoms — run a mix of modern
and legacy systems. Legacy Windows systems, unpatched network devices, and
default-credential routers are common in the infrastructure SOC teams protect.
Understanding system attack vectors means knowing where to look when an alert
fires: what service was targeted, what vulnerability was likely exploited, and
what the attacker would do next after gaining access.

---

## What I Want to Learn Next Based on This

The connection between this room and SIEM detection is direct: every system
attack technique leaves traces in logs. Brute force shows up as failed auth
events. Exploitation shows up as unusual process spawning or network connections.
Building detection rules for these patterns in Splunk is the practical extension
of what this room taught conceptually.

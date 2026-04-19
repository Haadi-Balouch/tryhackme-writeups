# IDS Fundamentals

**Platform:** TryHackMe | **Module:** Network Security | **Difficulty:** Easy
**Room Link:** https://tryhackme.com/room/idsfundamentals

---
## What This Room Covers
Intrusion Detection System fundamentals — types of IDS, detection methodologies, and how IDS fits into the broader SOC monitoring architecture.

---
## Key Concepts Learned
**IDS vs IPS — detection vs prevention**
| | IDS | IPS |
|---|---|---|
| What it does | Detects and alerts | Detects and blocks |
| Placement | Passive — monitors copy of traffic | Inline — traffic passes through it |
| Response | Generates alert for analyst | Automatically drops malicious traffic |
| Risk | None — passive monitoring | Can block legitimate traffic (false positives) |

Both are deployed in mature environments. IDS alerts feed the SIEM. IPS provides automated response for well-understood, high-confidence threats.

**Detection methodologies**
- **Signature-based:** Matches traffic against known attack patterns. Fast, low false positives for known threats. Completely blind to novel attacks.
- **Anomaly-based:** Establishes baseline of normal behavior, alerts on deviations. Catches unknown attacks. Higher false positive rate during baseline learning period.
- **Hybrid:** Combines both — signature detection for known threats, anomaly detection for unknown.

**Network IDS (NIDS) vs Host IDS (HIDS)**
NIDS monitors network traffic at a segment or perimeter level — one sensor can cover an entire subnet. HIDS runs on individual endpoints monitoring local activity — file changes, process creation, log events. HIDS and EDR are closely related concepts. Mature SOC environments run both.

**Where IDS alerts fit in the SOC workflow**
IDS generates alerts that feed into the SIEM. An IDS alert is not a confirmed incident — it is an investigation trigger. The SOC analyst triage process applies: is this a true positive or a false positive? What additional context does the SIEM have around this alert?

---
## How This Applies to Real SOC Work
Understanding IDS architecture means understanding where detection data comes from. When investigating an alert tagged as coming from Snort (the IDS), I know it was network-based detection — which tells me to look at network logs, not endpoint logs, for confirmation.

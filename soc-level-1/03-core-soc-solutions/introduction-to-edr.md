# Introduction to EDR

**Platform:** TryHackMe
**Path:** SOC Level 1
**Module:** SOC Fundamentals
**Difficulty:** Easy
**Room Link:** https://tryhackme.com/room/introtoedrandxdr

---

## What This Room Covers

What Endpoint Detection and Response (EDR) tools are, how they work, and
how SOC analysts use them to monitor and investigate endpoint activity.

---

## Key Concepts Learned

**EDR fills the gap SIEM alone cannot cover.**
A SIEM ingests logs from many sources but is reactive — it analyzes what
already happened. An EDR agent sitting on an endpoint monitors behavior
in real time: process execution, file changes, registry modifications,
network connections made by specific processes. It is the difference between
watching logs after the fact and watching the endpoint live.

**Key EDR Capabilities**

| Capability | What It Does |
|---|---|
| Process monitoring | Records every process started, parent/child relationships |
| File monitoring | Detects new files created, modified, or deleted |
| Registry monitoring | Tracks registry changes (common malware persistence mechanism) |
| Network monitoring | Maps which process made which network connection |
| Memory analysis | Detects injected code in running processes |
| Response actions | Can isolate endpoint, kill process, or quarantine file remotely |

**Process trees are critical for investigation.**
An EDR shows not just what process ran, but what spawned it. A document
spawning PowerShell spawning a network connection is a classic malware
execution chain. Without the parent-child process relationship, that looks
like three unrelated events. With an EDR process tree, it is immediately
suspicious.

**Popular EDR platforms in the industry**
CrowdStrike Falcon, Microsoft Defender for Endpoint, SentinelOne, Carbon Black,
and Wazuh (open-source) are all widely deployed. Wazuh is particularly relevant
for my home lab — it provides EDR-like endpoint visibility at no cost.

---

## Hands-On Tasks

Explored EDR interface and investigated simulated endpoint alerts — reviewing
process trees, examining file creation events, and tracing network connections
back to their originating process.

---

## How This Applies to Real SOC Work

Modern SOC environments run EDR alongside SIEM. When a SIEM alert fires, the
first tool the analyst opens after the SIEM is often the EDR — to see what
was actually happening on the endpoint at the time of the alert. Knowing how
to navigate an EDR and what to look for is as fundamental as knowing SPL queries.

---

## What I Want to Learn Next Based on This

Installing Wazuh in my home lab will give me hands-on EDR experience on my
own infrastructure. Correlating Wazuh endpoint events with Splunk SIEM logs
for the same simulated attack will build the multi-tool investigation workflow
that real SOC work requires.

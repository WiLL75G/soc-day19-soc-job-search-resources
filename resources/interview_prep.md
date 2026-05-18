# SOC Analyst Interview Preparation Guide

## Overview

SOC analyst interviews test three things:
technical knowledge, analytical thinking, and communication.
You need to pass all three not just the technical part.

---

## The 3 Interview Types You Will Face

### Type 1 Technical Screen (Phone/Video)
- 30–45 minutes
- Basic networking, security fundamentals, SOC operations
- They want to know if you speak the language

### Type 2 Technical Panel (In Person/Video)
- 60–90 minutes
- Scenario based questions, tool knowledge, incident response
- They want to know if you can think like an analyst

### Type 3 Behavioural (HR Round)
- 30–45 minutes
- STAR method answers, culture fit, communication
- They want to know if you'll be a good teammate

---

## Must Know Technical Topics

### Networking Fundamentals
```
- OSI Model — all 7 layers and what happens at each
- TCP vs UDP — differences and use cases
- TCP 3-way handshake — SYN, SYN-ACK, ACK
- Common ports — 22 SSH, 80 HTTP, 443 HTTPS, 53 DNS,
  3389 RDP, 445 SMB, 25 SMTP, 3306 MySQL
- DNS — how it works, A records, MX records, TTL
- DHCP — how IP assignment works
- Subnetting basics — CIDR notation
- Firewalls — stateful vs stateless
```

### Security Fundamentals
```
- CIA Triad Confidentiality, Integrity, Availability
- Defence in depth layered security approach
- Least privilege give only the access needed
- Zero trust never trust, always verify
- Encryption symmetric vs asymmetric
- Hashing MD5, SHA256 what they are and why they matter
- PKI certificates and how HTTPS works
- MFA types and why it matters
```

### SOC Operations
```
- Alert triage P1, P2, P3, P4 severity levels
- True positive vs false positive how to determine
- Escalation when and how to escalate
- Incident response Prepare, Identify, Contain,
  Eradicate, Recover, Lessons Learned (PICERL)
- Chain of custody preserving evidence
- Ticketing logging every action taken
```

### Tools Knowledge
```
- SIEM Splunk, Microsoft Sentinel, IBM QRadar
- EDR CrowdStrike, Carbon Black, Microsoft Defender
- Wireshark packet capture and analysis
- Nmap port scanning and host discovery
- VirusTotal malware and IOC analysis
- MITRE ATT&CK framework for adversary techniques
```

---

## Top 20 SOC Interview Questions + Answers

### Question 1
**"Walk me through what you do when you receive a high severity alert."**

```
Answer framework:
1. Acknowledge the alert in the ticketing system
2. Review the alert details source IP, destination,
   rule triggered, timestamp
3. Check for false positive indicators
4. Enrich the IOCs VirusTotal, AbuseIPDB, Shodan
5. Correlate with other alerts is this isolated?
6. Contain if confirmed block IP, isolate host
7. Document every action taken
8. Escalate to Tier 2 if needed with full triage notes
```

---

### Question 2
**"What is the difference between a virus and a worm?"**

```
Virus: attaches to a legitimate file and requires
       human action to spread

Worm: self replicates across networks without
      human interaction more dangerous at scale
```

---

### Question 3
**"What is a false positive and how do you handle it?"**

```
A false positive is an alert that fires but does not
represent a real threat.

How to handle:
1. Investigate fully before declaring it a false positive
2. Document why it is a false positive
3. Tune the detection rule to reduce future false positives
4. Never dismiss an alert without investigation
```

---

### Question 4
**"Explain the OSI model."**

```
Layer 7 - Application  - HTTP, DNS, SMTP
Layer 6 - Presentation - Encryption, compression
Layer 5 - Session      - Session management
Layer 4 - Transport    - TCP, UDP, ports
Layer 3 - Network      - IP addressing, routing
Layer 2 - Data Link    - MAC addresses, switches
Layer 1 - Physical     - Cables, hardware
```

---

### Question 5
**"What would you do if you suspected an insider threat?"**

```
1. Do not confront the employee directly
2. Document all suspicious activity with timestamps
3. Escalate immediately to your manager and HR
4. Preserve all log evidence
5. Follow the organisation's insider threat procedure
6. Maintain confidentiality throughout the investigation
```

---

### Question 6
**"What is the difference between IDS and IPS?"**

```
IDS (Intrusion Detection System):
- Monitors and alerts does not block
- Passive it watches

IPS (Intrusion Prevention System):
- Monitors and blocks active response
- Can stop attacks in real time
```

---

### Question 7
**"How do you investigate a phishing email?"**

```
1. Do not click any links or open attachments
2. Analyse the email headers check sending IP,
   Reply-To, SPF/DKIM status
3. Check the sender domain on VirusTotal
4. Check any links on VirusTotal and URLScan.io
5. Check if other users received the same email
6. Quarantine the email at the gateway
7. Notify users who received it
8. Document and escalate
```

---

### Question 8
**"What is MITRE ATT&CK?"**

```
MITRE ATT&CK is a globally accessible knowledge base
of adversary tactics and techniques based on real-world
observations. SOC analysts use it to:
- Map detected activity to known attacker behaviour
- Identify gaps in detection coverage
- Communicate findings in a standardised way
- Build detection rules based on known TTPs
```

---

## STAR Method for Behavioural Questions

Use this structure for every behavioural answer:

```
S — Situation: Set the context
T — Task: What was your responsibility
A — Action: What did you specifically do
R — Result: What was the outcome
```

### Example "Tell me about a time you worked under pressure"

```
S: During my home lab project I was simulating a
   full SOC shift with 3 concurrent alerts firing

T: I needed to triage all 3 alerts, determine if
   they were related, and produce an incident report

A: I prioritised by severity, investigated each alert
   systematically, discovered all 3 were linked to
   the same Tor exit node, and correlated them into
   one incident

R: I documented a full attack chain from brute force
   to data exfiltration and produced a professional
   incident report that is now part of my portfolio
```

---

## Questions to Ask the Interviewer

Always ask questions it shows genuine interest:

```
1. What does a typical day look like for a Tier 1 analyst here?
2. What SIEM and tools does the team use?
3. How is escalation handled between Tier 1 and Tier 2?
4. What does the onboarding process look like?
5. What opportunities exist for professional development
   and certifications?
6. What is the biggest challenge the SOC team faces right now?
```

---

## Day Before Interview Checklist

```
[ ] Review your portfolio projects know every detail
[ ] Review the company's recent security news
[ ] Prepare 3 STAR method answers
[ ] Review OSI model, CIA Triad, incident response steps
[ ] Know your resume line by line
[ ] Prepare your "tell me about yourself" answer
[ ] Test your audio and video if remote
[ ] Get a good night's sleep
```

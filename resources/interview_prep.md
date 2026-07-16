# SOC Analyst Interview Preparation Guide

Three things get tested: technical knowledge, analytical thinking, communication.

Only one of them is technical, and it is the one candidates over prepare. Someone who knows less but explains their reasoning clearly beats someone who knows more and cannot walk through it. The interview is not a quiz. It is a demonstration of how you think out loud.

---

## The Three Interview Types

**Technical screen**, 30 to 45 minutes, phone or video. Networking, security fundamentals, SOC operations. They are checking whether you speak the language before spending a panel's time on you.

**Technical panel**, 60 to 90 minutes. Scenario questions, tool knowledge, incident response. They are checking whether you think like an analyst. This is where the job is won or lost.

**Behavioural**, 30 to 45 minutes, HR. STAR answers, culture fit. They are checking whether the team can work with you at 3am.

---

## Must Know Technical Topics

### Networking Fundamentals

```
OSI model, all 7 layers and what happens at each
TCP vs UDP, differences and use cases
TCP three way handshake, SYN, SYN-ACK, ACK
Common ports:
  22 SSH, 25 SMTP, 53 DNS, 80 HTTP, 443 HTTPS,
  445 SMB, 3306 MySQL, 3389 RDP
DNS, how resolution works, A records, MX records, TTL
DHCP, how IP assignment works and what it reveals
Subnetting, CIDR notation
Firewalls, stateful vs stateless
```

### Security Fundamentals

```
CIA triad, confidentiality, integrity, availability
Defence in depth, layered controls
Least privilege, only the access needed
Zero trust, never trust, always verify
Encryption, symmetric vs asymmetric
Hashing, MD5 vs SHA256 and why the difference matters
PKI, certificates, how HTTPS actually works
MFA, the types and why it breaks most attacks
```

### SOC Operations

```
Alert triage, severity levels and what drives them
True positive vs false positive, how you decide
Escalation, when and what goes in the handoff
Incident response lifecycle:
  Detection, triage, containment, investigation,
  eradication, recovery, lessons learned
Chain of custody, preserving evidence before remediation
Documentation, logging every action taken
```

### Tools

```
SIEM: Splunk, Microsoft Sentinel, IBM QRadar
EDR: CrowdStrike, Carbon Black, Microsoft Defender
Wireshark, packet capture and analysis
Nmap, port scanning and host discovery
VirusTotal, AbuseIPDB, IOC enrichment
MITRE ATT&CK, adversary technique mapping
```

Honest rule: know the difference between tools you have used and tools you have read about. If a JD names QRadar, CrowdStrike, or Defender XDR and you have not touched them, the answer is transferable SIEM and EDR concepts, not implied hands on. Getting caught inflating one tool costs you every other claim in the room.

---

## Interview Questions and Answers

### "Walk me through what you do when you receive a high severity alert."

The most common opener. They are watching for structure, not speed.

```
1. Acknowledge the alert in the ticketing system
2. Read the alert detail: source, destination, rule
   triggered, timestamp
3. Check for false positive indicators before anything else
4. Enrich the IOCs: VirusTotal, AbuseIPDB, internal context
5. Correlate: is this isolated, or has this source
   appeared before?
6. Contain if confirmed: block the source, isolate the host
7. Document every action as you take it
8. Escalate with full triage notes, not just the alert
```

Step 5 is the one that separates candidates. Anyone can triage an alert. Asking whether it connects to something else is what makes you useful.

---

### "What is the difference between a virus and a worm?"

```
Virus: attaches to a legitimate file, requires a human
       action to spread
Worm:  self replicating across the network, no human
       needed, which is why it scales
```

The distinction that matters operationally: a worm means containment is a race. A virus means containment is a search.

---

### "What is a false positive and how do you handle it?"

```
An alert that fired without a real threat behind it.

1. Investigate fully before calling it false
2. Document why it is false, not just that it is
3. Tune the rule so it does not fire on this again
4. Never dismiss an alert without investigation
```

The trap in this question is speed. The wrong answer is anything that sounds like you close alerts quickly. Alert fatigue is real and every SOC has it, but "I'd dismiss it" is the answer that ends the interview.

Step 3 is what they actually want to hear. A false positive that recurs is a rule problem, not an alert problem.

---

### "Explain the OSI model."

```
7  Application  - HTTP, DNS, SMTP
6  Presentation - Encryption, compression
5  Session      - Session management
4  Transport    - TCP, UDP, ports
3  Network      - IP addressing, routing
2  Data Link    - MAC addresses, switches
1  Physical     - Cables, hardware
```

Do not just recite it. Tie it to work: a MAC address is layer 2, which is why it identifies a device even when the IP changes. Ports are layer 4, which is why a firewall rule on 443 does not care what protocol is riding on it.

---

### "What would you do if you suspected an insider threat?"

```
1. Do not confront the employee
2. Document all activity with timestamps
3. Escalate to your manager and HR immediately
4. Preserve log evidence before anything changes
5. Follow the organisation's insider threat procedure
6. Maintain confidentiality throughout
```

This question is not testing investigation skill. It is testing whether you know this one is not yours to run. Legal and HR own it, and a Tier 1 analyst who starts digging on their own creates a problem the organisation cannot fix later.

---

### "What is the difference between IDS and IPS?"

```
IDS: monitors and alerts, sits passively out of band
IPS: monitors and blocks, sits inline
```

The real answer is the tradeoff. An IPS false positive blocks legitimate traffic and someone's day stops. An IDS false positive costs an analyst ten minutes. That is why plenty of mature environments still run detection in front of prevention.

---

### "How do you investigate a phishing email?"

```
1. Do not click anything
2. Analyse the headers: sending IP, Reply-To,
   SPF and DKIM status
3. Check the sender domain on VirusTotal
4. Check links on VirusTotal and URLScan, do not visit them
5. Check who else received it
6. Quarantine at the gateway
7. Notify recipients
8. Document and escalate
```

Two things to say out loud. The Reply-To is the most reliable indicator in the header, because the attacker needs replies to reach them and cannot fake that. And step 5 is the one that determines scope. Quarantining one email stops one victim. Finding the other twenty recipients is the incident.

---

### "What is MITRE ATT&CK?"

```
A knowledge base of adversary tactics and techniques
built from real world observation.

Used to:
- Map observed activity to known attacker behaviour
- Find gaps in detection coverage
- Communicate findings in a shared vocabulary
- Build detections against known TTPs
```

Do not stop at the definition. The gap analysis use is the one that shows you understand it as a tool rather than a poster: if a technique has no rule behind it, that gap is visible before an incident finds it for you.

---

## STAR Method

```
S  Situation, set the context
T  Task, what you were responsible for
A  Action, what you specifically did
R  Result, what came out of it
```

A is the section that carries the answer. Most people spend three sentences on S and one on A. Invert that.

### Example, "Tell me about a time you worked under pressure"

```
S: I ran a full SOC shift simulation with three alerts
   firing across an eight hour window
T: Triage all three, determine whether they were related,
   and produce an incident report
A: I prioritised by severity, worked each alert to a
   verdict, and recorded the IOCs into a shared table
   rather than closing each ticket separately. That is
   what surfaced the same Tor exit node in all three
R: I correlated them into one campaign, mapped the full
   chain from brute force to exfiltration, and produced
   the handoff package
```

The specific detail is what makes it land. "I correlated them" is a claim. "I recorded IOCs into a shared table rather than closing each ticket separately, and that is what surfaced it" is a method, and a method is what they are hiring.

Rule for STAR answers: they need a real artifact behind them. If you cannot name the IP, the rule, the event ID, or the finding, it is a story rather than evidence.

---

## Questions to Ask Them

These are part of the interview. They are the one unscripted signal you control.

```
1. What does a typical day look like for a Tier 1 analyst here?
2. What SIEM and tools does the team run?
3. How does escalation work between Tier 1 and Tier 2?
4. What does onboarding look like?
5. What development and certification support exists?
6. What is the biggest challenge the SOC faces right now?
```

Question 6 is the one that works. It is the only one that gets an honest answer, and what they say tells you whether the role is a job or a fire.

---

## Day Before Checklist

```
[ ] Review portfolio projects, know every detail
[ ] Know your resume line by line, every claim defensible
[ ] Read the company's recent security news
[ ] Prepare 3 STAR answers with real artifacts behind them
[ ] Review OSI model, CIA triad, IR lifecycle
[ ] Prepare your "tell me about yourself"
[ ] Know which tools you have used and which you have not
[ ] Test audio and video if remote
[ ] Sleep

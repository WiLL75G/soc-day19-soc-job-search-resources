# SOC Analyst Interview Preparation Guide

SOC interviews test more than technical knowledge.

Three areas matter:

1. Technical knowledge
2. Analytical thinking
3. Communication

Knowing an answer is useful.

Being able to explain how you reached it is what demonstrates analyst thinking.

---

## The Three Interview Types

### Technical Screen

Usually a shorter interview focused on foundational knowledge.

Common areas include:

- Networking
- Security fundamentals
- SOC terminology
- Basic investigation concepts
- Tools listed in the job description

The objective is usually to establish whether the candidate understands the fundamentals required for the role.

### Technical Panel

Often more scenario focused.

Questions may cover:

- Alert triage
- Incident response
- Investigation methodology
- SIEM usage
- Network analysis
- Endpoint evidence
- Escalation decisions

The important part is not only reaching the correct conclusion.

Explain the evidence you would examine and why.

### Behavioural Interview

Behavioural interviews focus on how you communicate, work with others, handle problems, and learn.

The STAR method can help structure these answers.

---

## Must Know Technical Topics

### Networking Fundamentals

```text
OSI model and the purpose of each layer

TCP vs UDP

TCP three way handshake
SYN, SYN ACK, ACK

Common ports
22    SSH
25    SMTP
53    DNS
80    HTTP
443   HTTPS
445   SMB
3306  MySQL
3389  RDP

DNS resolution
A records
MX records
TTL

DHCP
IP assignment
Lease information
Hostname and MAC correlation

Subnetting
CIDR notation

Stateful vs stateless firewalls
```

Do not only memorize definitions.

Connect networking concepts to investigations.

For example, an IP address may be dynamically assigned. DHCP evidence can provide additional context such as a hostname and MAC address associated with that lease during the observed period.

---

## Security Fundamentals

```text
CIA triad
Confidentiality
Integrity
Availability

Defence in depth

Least privilege

Zero trust concepts

Symmetric and asymmetric encryption

Hashing

PKI and certificates

Multifactor authentication
```

The goal is to understand what these concepts mean operationally rather than only memorizing definitions.

---

## SOC Operations

```text
Alert triage

Severity and priority

True positive
False positive

Escalation

Incident response

Evidence preservation

Documentation

IOC enrichment

Event correlation

Investigation scoping
```

A useful investigation habit is separating:

```text
Observed
Inferred
Unknown
```

That prevents assumptions from becoming conclusions.

---

## Tools

Common SOC and investigation tools include:

```text
SIEM
Splunk
Microsoft Sentinel
IBM QRadar

EDR
Microsoft Defender
CrowdStrike
Carbon Black

Network analysis
Wireshark

Network discovery
Nmap

Threat intelligence
VirusTotal
AbuseIPDB

Frameworks
MITRE ATT&CK
```

### Honest Tool Rule

Know the difference between tools you have actually used and tools you have only studied.

If an employer asks about a product you have not used, explain the transferable concepts you understand instead of implying hands on experience.

For example:

> I have not used QRadar directly, but I have worked with Splunk and understand the SIEM workflow of searching telemetry, correlating events, investigating alerts, and documenting findings.

That is stronger than overstating experience.

---

# Common SOC Interview Questions

## "Walk me through what you would do when you receive a high severity alert."

A structured answer could be:

```text
1. Review the alert details.

2. Identify the source, destination, affected asset,
   timestamp, detection rule, and available context.

3. Validate the underlying telemetry.

4. Look for evidence that could explain the activity.

5. Enrich relevant indicators when appropriate.

6. Correlate the alert with surrounding activity.

7. Determine scope.

8. Document the evidence and current assessment.

9. Follow the organisation's containment and
   escalation procedure based on the evidence.
```

Containment should follow the organization's process and the evidence available.

A high severity label alone does not automatically establish compromise.

---

## "What is the difference between a virus and a worm?"

```text
Virus

Malicious code that typically attaches to or modifies
another file or program and depends on execution to
activate or propagate.

Worm

Malware designed to self propagate between systems,
often using network accessible vulnerabilities or
services without requiring the same user driven
distribution mechanism.
```

The operational difference matters because self propagating malware can expand scope rapidly.

---

## "What is a false positive and how do you handle it?"

A false positive occurs when a detection fires on activity that investigation determines is benign.

```text
1. Investigate before assigning the verdict.

2. Document the evidence supporting the benign
   explanation.

3. Determine whether the activity is isolated or
   repeatable.

4. If a repeatable benign pattern exists, document
   the pattern and recommend tuning through the
   organisation's detection engineering process.

5. Close or escalate according to procedure.
```

A Tier 1 analyst may identify and document a tuning opportunity without necessarily having authority to modify the production rule.

One false positive is also not automatically enough evidence to justify suppressing future alerts.

---

## "Explain the OSI model."

```text
7  Application     HTTP, DNS, SMTP

6  Presentation    Encoding, encryption, data formatting

5  Session         Session establishment and management

4  Transport       TCP, UDP, ports

3  Network         IP addressing and routing

2  Data Link       Frames, MAC addressing

1  Physical        Physical transmission media and signals
```

Do not stop at memorizing the seven layers.

Connect them to investigations.

For example, IP addresses operate at Layer 3 while TCP and UDP ports operate at Layer 4.

Understanding that distinction helps when interpreting packet captures and firewall activity.

---

## "What would you do if you suspected an insider threat?"

```text
1. Do not confront the person.

2. Preserve relevant evidence.

3. Document observations carefully.

4. Maintain confidentiality.

5. Follow the organisation's insider threat and
   escalation procedures.

6. Involve the appropriate authorized teams.
```

Ownership varies between organizations.

The important principle is not to independently expand a sensitive investigation outside your authority.

---

## "What is the difference between IDS and IPS?"

```text
IDS

Detects suspicious activity and generates alerts.

IPS

Can detect suspicious activity and take preventive
action because it operates inline with traffic.
```

The operational difference includes the impact of false positives.

An incorrect IPS decision can interrupt legitimate traffic.

An IDS alert normally requires investigation before action is taken.

---

## "How would you investigate a phishing email?"

```text
1. Preserve the message and avoid interacting with
   suspicious links or attachments.

2. Review available email headers.

3. Examine sender and Reply To information.

4. Review authentication results such as SPF, DKIM,
   and DMARC when available.

5. Extract relevant domains, URLs, IP addresses,
   attachment hashes, and other indicators.

6. Enrich indicators using appropriate threat
   intelligence sources.

7. Determine whether other recipients received the
   message.

8. Review available endpoint, email gateway, proxy,
   or identity telemetry for evidence of interaction.

9. Determine scope and document the findings.

10. Follow the organisation's quarantine,
    containment, and escalation procedures.
```

A mismatch between `From` and `Reply-To` can be useful evidence, but neither field should be treated as inherently trustworthy.

Scope also matters.

Finding one malicious email does not answer whether the same campaign reached additional recipients.

---

## "What is MITRE ATT&CK?"

MITRE ATT&CK is a knowledge base used to describe adversary tactics and techniques based on observed behaviour.

It can help analysts:

```text
Map observed behaviour

Communicate findings using shared terminology

Understand detection coverage

Identify coverage gaps

Support detection engineering

Organize threat behaviour
```

ATT&CK should describe behaviour supported by evidence.

A malware family being capable of a technique does not mean that technique occurred in the investigated activity.

---

# STAR Method

```text
S  Situation

T  Task

A  Action

R  Result
```

The Action section should explain what you specifically did.

Avoid spending most of the answer describing the background.

---

## Example

### "Tell me about a time you worked through multiple security alerts."

**Situation**

I completed a SOC shift simulation involving three alerts across a simulated workday.

**Task**

I needed to triage the alerts independently, determine whether any were related, document the evidence, and prepare a handoff.

**Action**

I investigated each alert separately before correlating their indicators.

I recorded the important IP addresses, affected systems, and investigation findings rather than treating each alert as an isolated ticket.

That exposed two different relationships.

The first two alerts shared the same external IP address.

The first and third alerts involved the same internal host.

I treated those relationships differently because the external IP was a Tor exit node, making that correlation weaker than the shared affected endpoint.

**Result**

The three alerts were documented as a correlated incident scenario with the strength of each relationship clearly explained and an end of shift handoff prepared.

---

The useful part of that answer is not:

> I correlated three alerts.

It is explaining **how** the correlation was discovered and why one relationship was stronger than another.

Use portfolio projects this way.

They provide real artifacts behind interview answers without implying professional SOC experience.

---

# Questions to Ask the Employer

Useful questions include:

```text
1. What does a typical day look like for a Tier 1
   analyst on this team?

2. Which SIEM, EDR, and case management tools does
   the SOC use?

3. How does escalation work between Tier 1 and
   Tier 2?

4. What does onboarding look like for a new analyst?

5. What training and certification support is
   available?

6. What are some of the biggest operational
   challenges the SOC is currently working through?
```

The answers can reveal how the SOC operates, what analysts are expected to handle, and how much support exists for development.

---

# Day Before Checklist

```text
[ ] Review the job description

[ ] Review portfolio projects relevant to the role

[ ] Know every claim on the CV

[ ] Research the company and its security services

[ ] Prepare three STAR examples backed by real work

[ ] Review networking and security fundamentals

[ ] Prepare a concise introduction

[ ] Know which tools you have used directly

[ ] Know which tools you have only studied

[ ] Prepare questions for the interviewer

[ ] Test audio and video for a remote interview
```

---

# Final Principle

Do not try to sound like an analyst with years of experience.

Explain the work you have actually done.

When answering a technical question, move through:

```text
What I observed
      ↓
What I would investigate
      ↓
What evidence I would validate
      ↓
What I can conclude
      ↓
What remains unknown
      ↓
What I would document or escalate
```

The objective is not to memorize the perfect interview answer.

It is to make your reasoning clear, evidence based, and defensible.

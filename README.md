# SOC Analyst Job Search Resources

Three resources for getting hired: where the jobs actually are, which certifications signal what, and how to answer the questions before someone asks them.

## What This Is

The technical work opens doors. It does not walk you through them.

Job searching is a separate skill from the job. Knowing which platforms surface real entry level roles, which certifications a hiring manager actually scans for, and how to talk about your own work under pressure are three different competencies, and none of them get built by writing detection rules.

This is a personal reference hub, not a portfolio piece. Written to be used, not to be read by a recruiter.

## Job Boards and Search Strategy

[resources/job_boards.md](resources/job_boards.md)

15 plus platforms curated for cybersecurity and SOC roles, tiered by how useful they actually are for someone without experience.

Also inside: the companies that hire junior analysts and why, search terms that surface the right roles on each platform, alert setup for LinkedIn, Indeed, and Google, application timing and volume rules, and 2026 salary ranges across the tiers.

What matters most:

MSSPs are the entry point. They hire Tier 1 at volume because their model depends on it, and they will take someone with lab work and no experience where an in house SOC will not.

Speed beats polish. Applying inside 24 hours of a posting puts you in the pile a recruiter is actually reading. Week two is a different queue.

The portfolio works while you sleep. It is the only part of the search that generates inbound rather than outbound.

## Certification Roadmap

[resources/certification_roadmap.md](resources/certification_roadmap.md)

Sequenced by hiring priority rather than listed by prestige.

Year 1, get hired: Security+, TryHackMe SOC Level 1, Blue Team Labs Online, Network+ optional.

Year 1 to 2, grow in role: CySA+, Splunk Core or SC-200.

Year 2 to 3, level up: SANS GIAC GSEC.

Each entry carries cost, prep time, and free study resources.

What matters most:

Security+ is the filter. For this roadmap, it is the first certification priority. It will not teach you the SOC job, but it can help get the application through an initial screen.

TryHackMe SOC Level 1 gives you something to say. A cert proves you studied. A completed path gives you a story about doing.

Splunk and SC-200 pay off after the first role, not before. Get hired, find out what the SOC actually runs, then certify on that.

## Interview Preparation

[resources/interview_prep.md](resources/interview_prep.md)

The three interview types: technical screen, panel, behavioural.

Must know topics across networking, security fundamentals, SOC operations, and tooling. Top 20 questions with structured answers. STAR framework with a worked example built on a real project. Six questions to ask them. Day before checklist.

What matters most:

Three things get tested, and only one is technical. Knowledge, analytical thinking, and communication. Candidates who can only do the first one lose to candidates who can do all three less well.

STAR answers need real artifacts behind them. "I would investigate the source IP" is theory. "I pulled the PCAP, filtered on the C2, and the DHCP hostname gave me the machine" is evidence, and it is the same answer with a spine.

The questions you ask are part of the interview. They are the only unscripted signal you control.

## Resources

- [Job Boards and Strategy](resources/job_boards.md)
- [Certification Roadmap](resources/certification_roadmap.md)
- [Interview Prep Guide](resources/interview_prep.md)

## Lessons Learned

The certification roadmap's own summary and its priority order disagreed with each other for a while, different phase labels, different year ranges, same certifications. Nobody reading either section alone would have caught it, only reading both side by side did. That is a small version of the same discipline the technical labs are built around: a document that contradicts itself is a document nobody has actually reread since writing it.

The GSEC cost line was a similar problem in a different shape. Quoting a single number for what is actually two different paths, a $999 standalone exam and a $7,000 plus training bundle, made a defensible fact read as a misleading one. Precision about what a number actually measures matters here the same way it matters in an investigation.

## What I Would Improve

I would source and date the job board and salary claims explicitly rather than stating them as flat facts, since both drift over time and a reader has no way to tell how current they are without a citation attached.

I would revisit this hub every few months. Certification pricing, exam codes, and which platforms surface real roles all change, and a career resource that goes stale quietly is worse than one that admits it needs a refresh date.

## Repository Structure

```
job-search-resources/
├── README.md
└── resources/
    ├── job_boards.md
    ├── certification_roadmap.md
    └── interview_prep.md
```

---

[![LinkedIn](https://img.shields.io/badge/LinkedIn-WilliamInCyber-blue?style=flat&logo=linkedin)](https://linkedin.com/in/WilliamInCyber) [![X](https://img.shields.io/badge/X-WilliamInCyber-black?style=flat&logo=x)](https://x.com/WilliamInCyber)

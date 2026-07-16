# Lab GRC02 — Security Assurance Ticket Queue Simulation

**Author:** Kiara Earl
**Purpose:** Practice the intake, triage, and resolution workflow used by security
assurance and GRC teams — reviewing incoming requests, prioritizing work, resolving
routine items independently, and knowing when something needs to be escalated. Built in
a ServiceNow PDI using the Incident table, since the workflow mechanics (intake,
categorize, prioritize, resolve, escalate) map the same way regardless of whether the
underlying table is called Incident or Case.

**Why this lab:** Security assurance operations is a skill set that doesn't get much
attention in typical homelab content, which tends to focus on SOC/blue-team work. This
lab builds hands-on reps at the actual day-to-day of that role: working a queue,
deciding what's routine versus what needs to go up the chain, and writing resolutions
that hold up to scrutiny. It uses realistic ticket content and draws on evidence I
already developed in Lab GRC01 and my homelab experiments as the answer bank.

---

## Ticket Categories Simulated

| # | Type | Description |
| --- | --- | --- |
| 1 | Customer Security Questionnaire | SIG Lite-style question about encryption standards |
| 2 | Audit Evidence Request | Access control review evidence |
| 3 | Audit Evidence Request | Incident response plan and tested incident evidence |
| 4 | Internal Documentation Maintenance | Security policy repository currency check |
| 5 | Vendor Risk / Third-Party Assurance | New subprocessor evaluation request |
| 6 | Escalation-Worthy Item | Legal/contractual breach notification SLA commitment |

---

## Triage / Priority Matrix

| | Low Complexity | High Complexity |
| --- | --- | --- |
| **High Urgency** | Resolve same-day | Escalate immediately |
| **Low Urgency** | Resolve within SLA, batch with similar requests | Research and draft response, flag for review |

**Mapped to each ticket:**

| Ticket | Urgency | Complexity | Action |
| --- | --- | --- | --- |
| 1. Encryption questionnaire | Low | Low | Resolve independently |
| 2. Access control evidence | Medium | Low | Resolve independently |
| 3. IR plan + tested incident | High | Low | Resolve same-day |
| 4. Doc repository maintenance | Low | Medium | Resolve, update tracked over time |
| 5. Vendor risk questionnaire | Low | High | Draft partial answer, flag gap |
| 6. Breach SLA legal commitment | High | High | Escalate to senior team member |

**Note on ServiceNow field mapping:** this PDI's Incident table uses native Impact and
Urgency fields rather than a custom Complexity field. Impact was repurposed to represent
task complexity (how much research/evidence-gathering the ticket requires) rather than
its default meaning of "how many users are affected." This is a reasonable adaptation —
the underlying triage logic is what matters, not the literal field label.

---

## Ticket 1 — Customer Security Questionnaire: Encryption Standards

**Request:** "Does your organization encrypt data at rest and in transit? Please describe
your encryption standards."

**Triage:** Impact 3-Low, Urgency 3-Low. Resolved independently, same session.

**Resolution:**

> Data in transit is encrypted using TLS 1.2 or higher for all customer-facing and
> internal communications, consistent with NIST SP 800-52 guidance on approved TLS
> configurations. Remote administrative access is secured using SSH key-based
> authentication (ed25519) with password authentication disabled. Data at rest
> protections follow data classification standards (public/internal/confidential/
> restricted), with restricted-tier data protected consistent with HIPAA's Security
> Rule technical safeguards (45 CFR § 164.312(e)(2)(ii)).

**Evidence source:** WGU D828 TLS/encryption remediation analysis; homelab Exp002 (SSH
key-based authentication hardening).

**Resolution code:** Solution provided

![Ticket 1 resolved](images/lab02-01-ticket1-resolved.png)

---

## Ticket 2 — Audit Evidence Request: Access Control Reviews

*In progress.*

---

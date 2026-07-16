# Lab GRC04 — Security Documentation Repository Index

**Author:** Kiara Earl
**Purpose:** Build a structured index that maps every control domain and topic covered
across this repository's labs back to its underlying evidence source — homelab
experiment or GRC lab — so evidence can be located quickly rather than re-derived each
time it's needed. This lab doesn't simulate a new scenario; it organizes and
consolidates the evidence produced by GRC01–GRC03 and the homelab-build repository into
one navigable reference.

**Why this lab:** A security documentation set is only as useful as its
findability. Across GRC01–GRC03, the same pieces of evidence get reused repeatedly —
Active Directory's least-privilege structure supports a framework mapping in GRC01 and
answers a live audit ticket in GRC02; the Third-Party Assurance gap identified in GRC01
resurfaces in GRC02 and is finally closed in GRC03. That reuse pattern is real and
valuable, but it's currently scattered across separate write-ups. This lab makes it
explicit and searchable, which is itself a core GRC/security assurance skill:
maintaining an evidence repository that a new team member or auditor could actually
navigate.

---

## Repository Index

This table maps each control domain or topic area covered across this repo's labs
back to its evidence source — homelab experiment or GRC lab — so evidence can be
located quickly rather than re-derived each time it's needed.

| Control Domain / Topic | Evidence Source | What It Proves |
| --- | --- | --- |
| Perimeter security / firewall rules | homelab-build Exp001 (pfSense) | Default-deny posture with explicit allow rules |
| Remote access hardening | homelab-build Exp002 (SSH hardening) | Key-based authentication, password auth disabled |
| Intrusion prevention | homelab-build Exp003 (fail2ban) | Automated response to brute-force attempts |
| Security monitoring / SIEM | homelab-build Exp004 (Splunk), Exp007 (Sentinel) | Centralized log visibility, alerting on attack patterns |
| Vulnerability management | homelab-build Exp005 (Nessus) | Authenticated and unauthenticated scanning capability |
| Identity and access management | homelab-build Exp006 (Active Directory) | Least-privilege OU/group structure, NIST SP 800-53 AC-6 |
| Threat detection, MITRE mapping | homelab-build Exp007 (Sentinel analytics rule) | Detection mapped to MITRE ATT&CK T1110 |
| DNS security / content filtering | homelab-build Exp008 (Pi-hole) | Malicious domain sinkholing |
| Incident response lifecycle | homelab-build Exp009 (CIC Incident Ops) | Tested incident, SITREP, break/fix runbook, exec summary |
| Encryption standards (transit/rest) | GRC02 Ticket 1; WGU D828 | TLS 1.2+, HIPAA Security Rule technical safeguards |
| Access control review evidence | GRC02 Ticket 2 | Biannual AD review cadence, NIST SP 800-53 AC-6 |
| IR plan + tested incident evidence | GRC02 Ticket 3 | Audit-ready evidence package for IR maturity |
| Framework crosswalk (19 domains) | GRC01 (HITRUST CSF mapping) | 14/19 domains mapped; establishes baseline coverage |
| Documentation currency review | GRC02 Ticket 4 | Process for validating docs stay current against framework |
| Vendor/third-party risk methodology | GRC03 | Gap analysis, risk tiering, conditional-approval framework, NIST SP 800-53 SA-9 |
| Escalation judgment (legal/contractual) | GRC02 Ticket 6 | Recognizing scope limits, routing to appropriate authority |

---

## Cross-Reference Notes

Several pieces of evidence get reused across multiple labs rather than re-derived each
time — this section traces those chains so the reuse pattern is explicit rather than
scattered.

- **Exp002 (SSH hardening) → GRC01 (HITRUST mapping) → GRC02 Ticket 1** — the same
  underlying control (key-based SSH authentication) supports a framework crosswalk
  entry and later answers a live encryption/access questionnaire without needing new
  evidence.
- **Exp006 (Active Directory) → GRC01 → GRC02 Ticket 2** — least-privilege OU structure
  is mapped once against NIST SP 800-53 AC-6 in GRC01, then cited directly as audit
  evidence in a ticket response rather than re-explained.
- **Exp007 (Sentinel) + Exp009 (CIC Incident Ops) → GRC02 Ticket 3** — the tested
  incident and its full lifecycle documentation (SITREP, runbook, exec summary) serves
  as the audit evidence for incident response maturity.
- **GRC01's unmapped domains → GRC02 Ticket 5 → GRC03** — Third-Party Assurance is
  flagged as a coverage gap in GRC01, resurfaces as a blocking issue in a live ticket
  scenario in GRC02, and is the direct reason GRC03 exists. This is the clearest
  example in the repo of a gap being identified, encountered again in practice, and
  then closed.
- **GRC02 Ticket 6 → GRC03's breach notification recommendation** — the judgment call
  to escalate rather than commit to a legal SLA in GRC02 is reused as the stated
  rationale for the same handling in GRC03's vendor risk recommendation, showing
  consistent decision-making rather than one-off reasoning.

---

## Known Gaps

Consolidated from GRC01's framework mapping and GRC03's vendor risk conditions — these
are the open items across the whole portfolio, tracked here rather than left scattered
across individual lab write-ups.

| Gap | Source | Status |
| --- | --- | --- |
| Privacy Practices (HITRUST domain) | GRC01 | Unmapped — no lab currently addresses this |
| Physical and Environmental Security (HITRUST domain) | GRC01 | Unmapped — not applicable to homelab environment as currently scoped |
| Business Continuity (HITRUST domain) | GRC01 | Unmapped — planned as a future lab |
| Configuration Management (HITRUST domain) | GRC01 | Unmapped — partially touched by Azure DevOps work-in-progress, not yet formalized as a lab |
| Vendor SOC 2 delivery follow-up | GRC03 | Open condition — tracked for the vendor's stated 12-month timeline, not yet due |
| Vendor IR test requirement | GRC03 | Open condition — 90-day requirement from onboarding, not yet triggered |
| Vendor access review cadence | GRC03 | Open condition — contractual requirement stated, not yet verified in practice |

This list is the honest state of the portfolio, not a finished checklist — some of these
are intentionally out of scope for a homelab (physical security), others are real
planned work (business continuity), and the GRC03 items are conditions that wouldn't
actually close until a real onboarding timeline played out. Keeping them visible here
is itself a small piece of GRC practice: an evidence repository that only shows what's
done isn't as useful as one that also shows what's still open.

---

## Summary / Lessons Learned

This lab was different from GRC01–GRC03 in that it didn't produce new evidence — it
organized evidence that already existed. That turned out to be its own distinct skill.

**An index is only valuable if it's honest about gaps, not just complete about
coverage.** It would have been easy to build a table that only listed what's covered
and call it done. Including the Known Gaps section — pulling forward exactly what
GRC01 and GRC03 already flagged as unresolved — makes this index something a real
auditor could use, instead of a document that looks more finished than the underlying
program actually is.

**Reuse chains are evidence of a coherent program, not repetition.** Tracing how
Exp006's Active Directory work supports both a framework mapping and a live audit
ticket response isn't padding — it's the actual argument for why this portfolio holds
together as one body of work rather than four disconnected labs. A hiring manager
reading GRC01 through GRC04 in sequence should be able to see that argument without
having to piece it together themselves.

**This closes the planned lab set.** GRC01 established framework coverage. GRC02
proved the ticket workflow. GRC03 built the vendor risk methodology that GRC01 and
GRC02 both pointed toward. GRC04 ties all three together into something navigable.
Portfolio site and resume updates come next, now that the underlying lab work is
complete.
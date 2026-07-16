# Lab GRC03 — Vendor Risk Assessment

**Author:** Kiara Earl
**Purpose:** Practice the evaluator side of vendor/third-party risk assessment —
reviewing a vendor's self-reported security questionnaire, identifying gaps between
what's claimed and what's verified, assigning a risk tier, and producing a defensible
recommendation. This is the analytical counterpart to GRC02 Ticket 1, which answered a
questionnaire from the vendor's side; this lab evaluates one from the customer/GRC
analyst side instead.

**Why this lab:** GRC01's HITRUST CSF mapping identified Third-Party Assurance as one
of five unmapped control domains. GRC02 Ticket 5 surfaced that same gap again inside a
live ticket queue simulation, when a new subprocessor onboarding request couldn't be
fully resolved without a formal vendor risk process. This lab closes that gap directly
by building and applying an actual vendor risk assessment methodology, rather than
continuing to flag the same missing capability without addressing it.

---

## Vendor Questionnaire Responses — DataStream Analytics, Inc.

**Vendor:** DataStream Analytics, Inc.
**Service provided:** Cloud-based data analytics and reporting platform (subprocessor)
**Data access requested:** Customer usage data, account metadata; no direct access to
payment or authentication credentials
**Questionnaire submitted:** [date]
**Submitted by:** Vendor Security Team (self-attested, no independent verification)

---

**1. Does your organization have a formal information security program?**
> Yes. We follow internal security policies covering access control, data handling,
> and system monitoring. Policies are reviewed periodically.

**2. Do you hold a current SOC 2 Type II or equivalent independent attestation?**
> Not currently. We are in the process of preparing for a SOC 2 Type I audit, targeted
> for completion within the next 12 months. In the interim, we can provide our internal
> security policy documentation upon request.

**3. Describe your encryption standards for data in transit and at rest.**
> Data in transit is encrypted via HTTPS. Data at rest is stored in our cloud
> provider's infrastructure, which provides encryption by default.

**4. Do you have a documented incident response plan? Has it been tested in the last
12 months?**
> We have an internal incident response process. It has not been formally tested via
> tabletop exercise or simulation in the last 12 months, though our team has handled
> minor operational incidents as they arose.

**5. How is access to customer data restricted and reviewed?**
> Access is limited to engineering and support staff on an as-needed basis. Access
> reviews are conducted informally by team leads; there is no fixed review cadence
> currently documented.

**6. Do you use any subprocessors of your own for this service? If so, please list
them.**
> Yes, we use a third-party cloud hosting provider and a third-party email/notification
> service. We have not conducted formal security assessments of these subprocessors but
> rely on their public compliance certifications.

**7. Do you carry cyber liability insurance?**
> Yes, our organization carries a general cyber liability policy. Specific coverage
> limits are available upon request under NDA.

**8. Would you agree to a contractual breach notification requirement (e.g., notify
within 24-72 hours of a confirmed data breach)?**
> We would need to review specific contractual language, but are generally open to
> reasonable notification timelines.

---

## Risk Assessment

**Reviewed by:** Kiara Earl, Security Assurance Analyst (simulated role)
**Assessment date:** [date]
**Data classification in scope:** Customer usage data, account metadata — classified
Internal/Confidential per this organization's data classification standard (see GRC02
Ticket 1).

---

### Gap Analysis

| # | Area | Vendor Response | Gap Identified |
| --- | --- | --- | --- |
| 1 | Independent attestation | SOC 2 Type I "in progress," no current attestation | No third-party verification of security controls exists today. Self-attestation only. |
| 2 | Encryption standards | HTTPS in transit; cloud provider default encryption at rest | No specific protocol/version cited (e.g., TLS 1.2+). Relies entirely on cloud provider defaults with no vendor-level detail. |
| 3 | Incident response | Documented internally, untested in 12 months | Untested IR plans frequently fail during real incidents. No tabletop or simulation evidence. |
| 4 | Access control | Informal reviews, no fixed cadence | No defined review frequency means access drift (stale/excess permissions) is unmonitored. Directly conflicts with least-privilege expectations (NIST SP 800-53 AC-6). |
| 5 | Subprocessor oversight | Uses two subprocessors, no formal assessment performed | Fourth-party risk is unmanaged — vendor is relying on public certifications without independent validation, same weakness as Gap 1 one level removed. |
| 6 | Breach notification commitment | "Generally open" but non-committal | No firm SLA offered. This is the same class of gap flagged as escalation-worthy in GRC02 Ticket 6 — a commitment that requires contractual/legal precision, not a soft answer. |

### Risk Tier: **Medium-High**

**Rationale:** No control failure was identified — the vendor has *some* program in
place across every area reviewed. The risk driver is the absence of independent
verification anywhere in the response set. Every claim is self-attested: no completed
SOC 2, no tested IR plan, no fixed-cadence access reviews, no assessed subprocessors.
Individually, each gap is common for a smaller vendor still maturing its security
program. Collectively, they mean this vendor's security posture cannot currently be
independently confirmed, which is the core concern a vendor risk assessment exists to
catch — self-reported maturity is not the same as verified maturity.

Data sensitivity is a moderating factor: the vendor is not requesting access to
payment or authentication credentials, which keeps this out of High/Critical tier
despite the verification gaps.

### Recommendation: **Approve with Conditions**

Not a rejection — the data sensitivity doesn't warrant it, and immature-but-improving
vendors are common in practice. Not an unconditional approval either, given the
verification gaps identified. Recommended conditions prior to full onboarding:

1. Require submission of completed SOC 2 Type I report once available (per vendor's
   own stated 12-month timeline); flag for review at that milestone.
2. Request written confirmation of encryption protocol/version in use, not just method.
3. Require a documented incident response test (tabletop or simulation) within 90 days
   of onboarding, with evidence provided.
4. Establish a fixed access review cadence (e.g., quarterly) as a contractual
   requirement, mirroring this organization's own biannual AD review standard from
   GRC02 Ticket 2.
5. Request a list of subprocessor compliance certifications for reference, even if
   independent assessment isn't feasible at this stage.
6. Escalate the breach notification SLA question to legal/security leadership for
   contractual negotiation — consistent with how this exact issue was handled in GRC02
   Ticket 6 rather than settled informally here.

**Framework reference:** NIST SP 800-53 SA-9 (External System Services) — organizations
must establish requirements for external providers to comply with applicable security
requirements and employ mechanisms to monitor compliance. This assessment reflects
that standard: conditional approval paired with defined follow-up monitoring, not a
one-time pass/fail decision.

**Evidence source:** GRC01 (Third-Party Assurance identified as unmapped domain);
GRC02 Ticket 2 (access review cadence precedent), Ticket 5 (initial gap flag), Ticket 6
(breach SLA escalation precedent).

---

## Summary / Lessons Learned

This lab simulated the analyst side of vendor risk assessment — reviewing a
subprocessor's self-reported security questionnaire and producing an independent risk
determination, rather than answering a questionnaire about my own environment (as in
GRC02 Ticket 1).

A few things stood out:

**Self-attestation is not verification.** Every individual answer in the vendor's
questionnaire was plausible and not obviously deficient — a security program exists, data
is encrypted, an IR process exists. The risk wasn't in any single answer being wrong;
it was in the pattern of unverified claims across every category. Recognizing that
distinction — "this vendor has controls" versus "this vendor can prove it has controls"
— is the core judgment a vendor risk assessment is supposed to produce, and it's easy to
miss if each answer is evaluated in isolation instead of as a set.

**"Approve with conditions" is often the correct answer, not a compromise.** A binary
approve/reject framing doesn't fit most real vendor reviews. This vendor wasn't a
security risk severe enough to reject outright, but it also wasn't verified enough to
approve without follow-up. Conditional approval with defined milestones (SOC 2 delivery
date, IR test requirement, review cadence) is what lets onboarding proceed without
accepting unmanaged risk — and it mirrors how the triage matrix in GRC02 treated
high-complexity items: not resolved outright, not ignored, but handled with a clear
next step.

**This lab closed a gap instead of just naming one.** GRC01 identified Third-Party
Assurance as an unmapped HITRUST domain. GRC02 Ticket 5 surfaced it again as a live
gap in a simulated ticket queue. GRC03 is the first lab that actually builds the
missing capability — a working vendor risk evaluation methodology — rather than just
flagging that it's missing. That progression (identify a gap, encounter it again in
practice, then build the process that closes it) is a more realistic picture of how
GRC maturity actually develops than three unrelated labs would be.

**Framework citations earn their place when they change the outcome, not just support
it.** NIST SP 800-53 SA-9 wasn't cited to sound thorough — it's the specific control
that justifies why "approve with conditions plus ongoing monitoring" is the correct
structure, instead of a one-time pass/fail decision. Tying the recommendation format
itself back to a named control is what separates a risk opinion from a risk
assessment.

**Next:** Lab GRC04 (security documentation repository index) will build the
structured evidence index referenced throughout GRC01–GRC03 — turning the scattered
evidence sources cited across all three labs into one navigable reference.
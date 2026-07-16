# Compliance & GRC Labs

Ongoing documentation of hands-on GRC, audit support, and compliance framework work,
built to support security assurance, audit prep, and compliance-adjacent roles.

**Kiara Earl** — CompTIA A+ Certified | WGU B.S. Cybersecurity Student

---

## Why I Built This

My other repo, [homelab-build](https://github.com/kiaraearl/homelab-build), documents
infrastructure and SOC-style security engineering — firewalls, SIEM, Active Directory,
that kind of thing. This repo is different. It's about a skill that doesn't get much
attention in typical homelab content: taking security work you've already done and
mapping it to the compliance frameworks companies actually get audited against.

Every lab here pulls from real evidence, either hands-on homelab work or coursework from
my WGU program, and reframes it the way a GRC or security assurance team would actually
use it.

---

## Lab Goals

- [x] Map existing security control evidence to a major compliance framework (HITRUST CSF)
- [x] Simulate a security assurance ticket intake/triage workflow
- [x] Draft a vendor risk assessment questionnaire response
- [ ] Build a structured security documentation repository index

---

## Labs & Write-Ups

| # | Lab | Status | Write-Up |
| --- | --- | --- | --- |
| GRC01 | HITRUST CSF domain mapping — crosswalk of homelab controls and WGU D828 coursework against all 19 HITRUST domains | Complete | [View](labs/lab01-hitrust-csf-mapping/lab01-hitrust-csf-mapping.md) |
| GRC02 | Security assurance ticket queue simulation — intake, triage, and resolution workflow | Complete | [View](https://github.com/kiaraearl/compliance-grc-labs/blob/main/labs/lab02-security-assurance-ticket-queue/lab02-security-assurance-ticket-queue.md) |
| GRC03 | Vendor risk assessment — sample questionnaire response | Complete | [View](https://github.com/kiaraearl/compliance-grc-labs/blob/main/labs/lab03-vendor-risk-assessment/lab03-vendor-risk-assessment.md) |
| GRC04 | Security documentation repository — structured evidence index | Planned | — |

---

## Frameworks and Standards Referenced

| Framework / Standard | Where It Shows Up |
| --- | --- |
| HITRUST CSF | GRC01 — 19-domain control crosswalk |
| NIST Cybersecurity Framework | GRC01, via WGU D828 policy analysis |
| NIST SP 800-53 | GRC01, via WGU D828 (AC-6 Least Privilege analysis) |
| ISO/IEC 27001 | GRC01, via WGU D828 (Annex A data classification) |
| HIPAA / HITECH | GRC01, via WGU D828 (Security Rule, breach notification) |
| SOC 2 | Referenced in GRC01 relevance notes, deeper coverage planned |
| NIST SP 800-53 SA-9 | GRC03 — vendor/external system services risk assessment |

---

## Related Repositories

- [homelab-build](https://github.com/kiaraearl/homelab-build) — infrastructure, SIEM, and SOC-style security engineering
- [clickfix-ir-casestudy](https://github.com/kiaraearl/clickfix-ir-casestudy) — real-world incident response case study

---

## Author

**Kiara Earl**
CompTIA A+ Certified | WGU B.S. Cybersecurity & Information Assurance (Expected 2027)
kimearls24@outlook.com | Houston, TX
[Portfolio](https://kiaraearl.github.io) | [GitHub](https://github.com/kiaraearl)

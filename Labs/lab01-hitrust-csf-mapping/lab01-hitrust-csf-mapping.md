# Lab GRC01 — HITRUST CSF Control Mapping

**Author:** Kiara Earl
**Purpose:** Map existing homelab experiments (Exp001–Exp009) and WGU D828 (Legal Issues in
Information Security) coursework against the 19 HITRUST CSF assessment domains, to show
awareness of HITRUST as a framework that's built on top of NIST, ISO/IEC 27001, and HIPAA.

**Why HITRUST:** HITRUST CSF pulls together 44+ standards, including NIST CSF, NIST SP
800-53, ISO/IEC 27001, HIPAA, and PCI DSS, into 19 domains and 135 security controls.
Since I already had documented NIST/ISO/HIPAA analysis from D828 and hands-on control
work from the homelab, this mapping was mostly a crosswalk exercise rather than starting
from zero.

---

## Control Crosswalk

| # | HITRUST CSF Domain | Status | Evidence | Source |
| --- | --- | --- | --- | --- |
| 1 | Information Protection Program | Covered | Policy analysis applying NIST CSF (Identify/Protect/Detect/Respond/Recover) and ISO 27001 Annex A to a case-study organization's security policy | D828 QEN1 |
| 2 | Endpoint Protection | Covered | fail2ban intrusion prevention (maxretry 3, bantime 600, live-tested ban); Nessus vulnerability/malware-relevant scanning | Exp003, Exp005 |
| 3 | Portable Media Security | Gap | No lab evidence — no removable media control implemented | — |
| 4 | Mobile Device Security | Gap | No lab evidence — homelab is desktop/server only | — |
| 5 | Wireless Security | Gap | No lab evidence — homelab network is virtualized and wired | — |
| 6 | Configuration Management | Covered | pfSense default-deny firewall ruleset with explicit allow rules; sprint-tracked infrastructure changes in Azure DevOps | Exp001, AzDO lab |
| 7 | Vulnerability Management | Covered | Nessus Essentials Plus unauthenticated and credentialed scans with a dedicated RSA 4096 service account | Exp005 |
| 8 | Network Protection | Covered | pfSense perimeter firewall; Sentinel analytics rule detecting brute-force (MITRE T1110), High severity, 5-minute interval | Exp001, Exp007 |
| 9 | Transmission Protection | Covered | SSH hardening to key-only auth (ed25519); D828 remediation recommending TLS 1.2+ over deprecated SSL v2.0 | Exp002, D828 QEN1 |
| 10 | Password Management | Covered | SSH password auth disabled in favor of key-only; AD domain password policy across 3 OUs and 3 users | Exp002, Exp006 |
| 11 | Access Control | Covered | AD least-privilege OU structure; D828 analysis of NIST SP 800-53 AC-6 (Least Privilege) applied to case study | Exp006, D828 QEN1 |
| 12 | Audit Logging and Monitoring | Covered | Splunk SIEM (SSH Attack Monitor dashboard, fail2ban ban alert); Sentinel KQL queries against Log Analytics Workspace | Exp004, Exp007 |
| 13 | Education, Training, and Awareness | Covered | Formal coursework (D828) covering security frameworks, standards, and legal compliance requirements | D828 (WGU) |
| 14 | Third-Party Assurance | Gap, planned | Vendor risk assessment lab scheduled next — treating homelab tools as simulated third-party vendors | Planned — Lab GRC03 |
| 15 | Incident Management | Covered | Full incident lifecycle: Sentinel Incident #1 (confirmed brute-force), ServiceNow ticket lifecycle, SITREP and break/fix runbook | Exp007, Exp009 |
| 16 | Business Continuity and Disaster Recovery | Covered (analysis only) | D828 case-study analysis of DR policy: RTO/RPO, annual DRP testing, failover site design | D828 QEN1 |
| 17 | Risk Management | Covered | Nessus risk-based vulnerability scanning; D828 risk-based access control and audit analysis | Exp005, D828 QEN1 |
| 18 | Physical and Environmental Security | Gap | No lab evidence — homelab is virtualized, no physical facility control to demonstrate | — |
| 19 | Data Protection and Privacy | Covered | Pi-hole DNS-layer data protection; D828 HIPAA Security Rule and data classification (public/internal/confidential/restricted) analysis | Exp008, D828 QEN1 |

**Coverage: 14 of 19 domains with direct evidence, 1 domain planned (Third-Party
Assurance), 4 domains with no current evidence.**

---

## Gap Domains — Being Honest About It

I didn't want to stretch the evidence to make every domain look "covered," so here's
what's actually missing:

- **Portable Media, Mobile Device, and Wireless Security** — my homelab runs on
  VirtualBox over a wired virtual network, so there's nothing to point to here. Not
  planning a dedicated lab for these since it's a low-value build for the kind of role
  I'm targeting.
- **Physical and Environmental Security** — same problem. This one's really about
  physical facility controls, which a home lab just can't demonstrate.
- **Third-Party Assurance** — this one's actually planned. It's Lab GRC03 (vendor risk
  assessment), coming next.

## Why This Matters for the Role

The Information Security Analyst role at Machinify lists "assist with HITRUST r2 and
SOC 2 audit preparation and evidence collection" as roughly a quarter of the job. This
crosswalk is basically a small-scale version of that exact task: taking security control
evidence that already exists and mapping it to a specific framework's structure so it's
ready to hand to an auditor.

## References

- HITRUST Alliance. HITRUST CSF Domain Structure (19 domains, 135 security controls, 14 privacy controls).
- National Institute of Standards and Technology. (2018). *Framework for Improving Critical Infrastructure Cybersecurity* (Version 1.1).
- International Organization for Standardization. (2022). *ISO/IEC 27001:2022 Information security, cybersecurity and privacy protection*.
- U.S. Department of Health and Human Services. (1996). *Health Insurance Portability and Accountability Act (HIPAA)*.
- D828 — Legal Issues in Information Security, Western Governors University, QEN1 Task 1 (TeleMedica case study).

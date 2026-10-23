# GRC205 — Business Continuity and Disaster Recovery (BCDR) Report

**Institution:** International Cybersecurity and Digital Forensics Academy (ICDFA)  
**School:** School of Cyber Risk, Governance and Compliance  
**Program:** GRC Engineering (CGRCE)  
**Course:** GRC205 — Incident Management and Business Continuity  
**Assignment:** Business Continuity and Disaster Recovery  

---

## Student Information

| Field | Details |
| :--- | :--- |
| **Student** | Ibrahim Abdullahi |
| **Registration Number** | 2025/GCR/12720 |
| **Official Email** | gcr2512720@students.icdfa.edu.ng |
| **Cohort** | Batch B2025 |
| **Academic Session** | 2026 |
| **Level / Year** | Level 1 / Year 1 |

---

## Executive Summary & Scope

This report evaluates business continuity and disaster recovery (BCDR) arrangements for **Northbridge Skills Institute**, a fictional institution comprising 1,800 learners and 90 staff. 

### Scenario Context
* **Disruption Event:** 08:00 WAT on Monday (Day 0) — Flooding and a power outage render the main campus and locally hosted services unavailable.
* **Initial Closure Estimate:** 72 hours.
* **Current Operational State:**
  * Microsoft 365 email remains accessible via mobile internet.
  * Local applications depend on the recovery network and `AUTH01`.
  * Technical recovery activities are constrained to **two technicians**.
  * **Exam Emergency:** 120 candidates are scheduled for an 11:00 exam. 40 candidates require institution-provided workstations; however, only 25 are available at the alternative premises from 10:00 (a deficit of 15 workstations).
* **Cause:** Flooding (no confirmed cyberattack).

### Method & Frameworks
* **Planning Baseline:** Annual budget limit of **NGN 3,000,000**.
* **Methodology:** Informed by **NIST SP 800-34 Rev. 1** and **ISO 22301:2019 / Amd 1:2024**.
* *Note: Recovery objectives, control measures, and governance models are proposed academic recommendations subject to institutional review.*

---

## Task 1 — Business Impact Analysis (BIA)

Business priority is driven by time-sensitive consequences, learner welfare, and institutional integrity rather than hourly financial loss alone.

### Function Priority & Description
1. **F1 (Teaching/Assessment):** Highest priority. A failed 11:00 examination incurs immediate educational harm and a one-off rescheduling penalty.
2. **F2 (Fees/Finance) & F3 (Admissions):** High priority. Fee confirmation closes at 16:00 and admissions close at 18:00 on Day 0.
3. **F4 (Payroll):** Bank instructions due by 12:00 on Day 1.
4. **F5 (Certificates/Records):** Lowest default ranking; operates under a 48-hour internal commitment.

### Function Analysis Matrix

| Priority / Function | Owner | Affected Users & Constraints | Key Dependencies | Minimum Acceptable Service & Control |
| :--- | :--- | :--- | :--- | :--- |
| **1. F1 Teaching/Assessment** | Academic Director | 120 exam candidates; broader learners/tutors. 11:00 exam deadline. | Network, AUTH01, DB01, LMS01 | Accessible authorized delivery or equitable rescheduling, candidate authentication, invigilation, signed attendance, exam-integrity approval. |
| **2. F2 Fees/Finance** | Finance Manager | Payers / finance staff. 16:00 fee confirmation deadline. | Network, AUTH01, DB01, FIN01, Payment Provider | Provider-verified provisional acknowledgement, unique transaction IDs, dual review, and eventual reconciliation. |
| **3. F3 Admissions** | Registrar | Applicants / registrars. 18:00 registration close. | Network, AUTH01, DB01, REG01 | Time-stamped restricted intake with case references, authorized cutoff/appeal handling, duplicate and eligibility verification. |
| **4. F4 Payroll** | HR Manager | Up to 90 staff. Day 1 12:00 submission deadline. | Network, AUTH01, DB01, HR01, Bank | Last verified payroll plus approved amendments, independent HR/Finance sign-off, bank acknowledgement, duplicate prevention. |
| **5. F5 Certificates/Records** | Records Manager | Learners, alumni, staff. 48-hour internal commitment. | Network, AUTH01, FS01 | Restricted request queue; issue authentic records only against independently verified sources and Records Manager authority. |

### Financial Impact Model (Unmitigated Loss)

| Function | Hourly Impact Rate (NGN) | 8-Hour Worked Cost (NGN) | 24-Hour Worked Cost (NGN) |
| :--- | :--- | :--- | :--- |
| **F1** | 60,000 / h | 600,000 *(incl. 120k reschedule fee)* | 1,560,000 *(incl. 120k reschedule fee)* |
| **F2** | 40,000 / h | 320,000 | 960,000 |
| **F3** | 20,000 / h | 160,000 | 480,000 |
| **F4** | 10,000 / h | 80,000 | 240,000 |
| **F5** | 5,000 / h | 40,000 | 120,000 |
| **TOTAL** | **135,000 / h** | **1,200,000** | **3,360,000** |

*Key Technical Dependencies:* `DB01` (F1–F4), `AUTH01` (All functions), and the Recovery Network infrastructure.

---

## Task 2 — Recovery Objectives & Backup Design

### Target Recovery Metrics

| Function | RTO / Target Deadline | RPO Target | MTD / Buffer | Owner Acceptance Gate |
| :--- | :--- | :--- | :--- | :--- |
| **F1** | 2 h / 10:00 | 15 min | 3 h / 1 h | Academic Director certifies secure, accessible exam arrangements. If infeasible, record authorized reschedule and RTO breach. |
| **F2** | 4 h / 12:00 | 30 min | 8 h / 4 h | Finance accepts provider-confirmed provisional register with dual review. |
| **F3** | 6 h / 14:00 | 1 h | 10 h / 4 h | Registrar accepts timestamped, privacy-controlled admissions channel. |
| **F4** | 20 h / Day 1 04:00 | 4 h | 28 h / 8 h | HR and Finance dual-authorize verified bank file. |
| **F5** | 24 h / Day 1 08:00 | 24 h | 48 h / 24 h | Records Manager accepts secure queue and authenticated record checks. |

### Backup Checkpoint Analysis (Status at 08:00 Day 0)

| Checkpoint | Age at 08:00 | Status vs RPO |
| :--- | :--- | :--- |
| **B01 (DB01 Full, 23:00 Day -1)** | 9 h old | Base image alone cannot meet transactional RPOs. |
| **B02 (DB01 Incremental, 07:00 Day 0)** | 1 h old | Latest recoverable point if full contiguous chain passes. Exceeds F1 (15 min) and F2 (30 min) RPO targets. |
| **B03 (AUTH01 Snapshot, 00:00 Day 0)** | 8 h old | Exceeds conservative application RPOs for F1–F4. |
| **B04 (FS01 Full, 23:00 Day -1)** | 9 h old | Within F5 target allowance (24 h). |
| **Disconnected Full (17:00 Day -3)** | 63 h old | Emergency fallback only; non-compliant. |

### Proposed Backup Strategy
* **Database (`DB01`):** Weekly application-consistent full backups, daily differential backups, and 15-minute transaction log captures.
* **Identity (`AUTH01`):** System configuration and state capture after all changes and at regular daily intervals.
* **Files (`FS01`):** Weekly full backups and daily incremental version captures.
* **Retention Scheme:** 7 days local (fast restore), 35 days encrypted offsite, 12 months immutable monthly archive.
* **Restoration Chain Rule:** Require signed manifests, hash verifications, credentials/MFA segregation between production and backup platforms, and strict isolation testing.

---

## Task 3 — Strategy and Budget Evaluation

**Annual Budget Ceiling:** NGN 3,000,000  
**Fixed Requirements:** NGN 400,000 (Protected Backups) + NGN 200,000 (Training & Testing) = NGN 600,000 fixed overhead.

| Strategy Package | Base Cost + Fixed Overhead (NGN) | Total Cost / Budget Headroom | Est. First Service Recovery / Data Loss | Decision & Suitability |
| :--- | :--- | :--- | :--- | :--- |
| **Cold Site** | 600,000 + 600,000 | 1,200,000 / 1,800,000 | 24–48 h / Up to 24 h | **Unacceptable.** Cannot meet short F1/F2 objectives. |
| **Warm Site** | 1,500,000 + 600,000 | **2,100,000 / 900,000** | **3–5 h / 1–6 h** | **RECOMMENDED.** Feasible foundation; leaves NGN 900k operational headroom for temporary device acquisition/workarounds. |
| **Hot Site** | 2,400,000 + 600,000 | 3,000,000 / 0 | ~1 h / Up to 15 min | **High Risk.** Consumes 100% of budget with zero contingency for auxiliary hardware or unforeseen costs. |

---

## Task 4 — Coordinated BCDR Plan

### RACI Governance Matrix

* **A** - Accountable | **R** - Responsible | **C** - Consulted | **I** - Informed

| Activity | Responsible (R) | Accountable (A) | Consulted / Informed |
| :--- | :--- | :--- | :--- |
| **Plan Activation** | BC Coordinator | Incident Commander | **C:** Facilities, DR, Academic \| **I:** All staff |
| **Exam Delivery / Reschedule** | Academic Director, BC | Incident Commander | **C:** Facilities, Security \| **I:** Learners |
| **Backup Validation** | DR Technicians | DR Lead | **C:** Security, Business Owners \| **I:** BC |
| **Infra & App Restoration** | DR Technicians | DR Lead | **C:** Security, Owners \| **I:** Incident Commander |
| **Communications** | Communications Lead | Incident Commander | **C:** Academic, Facilities, Security \| **I:** Stakeholders |
| **Financial Reconciliation** | Finance Staff | Finance Manager | **C:** DR, Payment Provider \| **I:** Incident Commander |
| **Payroll Processing** | HR & Finance Staff | HR Manager | **C:** Bank, Security \| **I:** Incident Commander |
| **Return to Primary Site** | BC, Facilities, DR, Owners | Incident Commander | **C:** Security, Communications \| **I:** All users |

### Disaster Recovery Sequencing (Technical Runbook)

1. **Network (30 min):** Establish safe alternate site connectivity, routing, and basic security. *(Technician 1)*
2. **AUTH01 (30 min):** Verify identity system, trusted accounts, and access permissions. *(Technician 1)*
3. **Backup Integrity (30 min):** Independent access checks and B01+B02 chain verification. *(DR Lead)*
4. **DB01 Restoration (90 min):** Apply full backup and ordered incrementals; execute integrity scripts. *(Technician 1)*
5. **FS01 Restoration (60 min):** Restore file system and validate permissions. *(Technician 2 — runs parallel with step 4)*
6. **Application Service Restoration:**
   * `FIN01` (30 min) — *Technician 2*
   * `LMS01` (45 min) — *Technician 1*
   * `HR01` (45 min) — *Technician 2*
   * `REG01` (30 min) — *Technician 1*
7. **Business Acceptance & Cutover:** Owners certify usability, controls, and data integrity prior to operational handoff.

---

## Task 5 — Recovery Schedule & Simulated Tabletop Exercise

### Critical Path Timeline (Two-Technician Model)

```
08:00                08:30                09:00                09:30                               11:00                11:30        11:45        12:15
  |--- Network (T1) ---|--- AUTH01 (T1) ----|-- Sec Checks (T1) -|---------- DB01 Restore (T1) ------|--- LMS01 (T1) -----|--- REG01 (T1) ------------|
                       |                    |                    |                                   |
                       |                    |                    |--- FS01 (T2) ---|                 |--- FIN01 (T2) ----|--- HR01 (T2) -------------|
```

* **Assessment Critical Path:** Network (30m) $\rightarrow$ AUTH01 (30m) $\rightarrow$ Checks (30m) $\rightarrow$ DB01 (90m) $\rightarrow$ LMS01 (45m) = **225 minutes (3h 45m)**.
* **Earliest LMS01 Technical Completion:** 11:45 WAT (Misses 11:00 exam start by 45 minutes; RTO breached).
* **Overall System Restoration Finish:** 12:15 WAT (Elapsed time: 4 hours 15 minutes).

### Performance Metrics Summary

| Function | Technical Finish | Elapsed Time | RTO Target / Result | MTD Target / Result | RPO Target / Result |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **F1** | 11:45 | 3 h 45 min | 2 h (**MISSED** by 1h 45m) | 3 h (**MISSED** by 45m) | 15 min (**EXCEEDED** — 1h age) |
| **F2** | 11:30 | 3 h 30 min | 4 h (**MET**) | 8 h (**MET**) | 30 min (**EXCEEDED** — 1h age) |
| **F3** | 12:15 | 4 h 15 min | 6 h (**MET**) | 10 h (**MET**) | 1 h (**MET**) |
| **F4** | 12:15 | 4 h 15 min | 20 h (**MET**) | 28 h (**MET**) | 4 h (**MET**) |
| **F5** | 10:30 | 2 h 30 min | 24 h (**MET**) | 48 h (**MET**) | 24 h (**MET**) |

### Tabletop Stress Scenario (45-Minute Simulated Inject Log)

| Inject Time | Event / Inject | Decision & Action Taken |
| :--- | :--- | :--- |
| **Min 10** | Closure extended from 72h to 5 days. | Incident Commander authorizes extended site contract (120h). |
| **Min 20** | Available exam workstations drop from 25 to 15. | Workstation deficit increases to 25. Academic Director initiates equitable emergency reschedule protocol. |
| **Min 30** | DB01 incremental fails integrity; suspicious admin login detected. | DR Lead rejects chain; IR preserves forensic evidence. Revert to DB01 Full (23:00 - 9h data loss) subject to risk sign-off. |
| **Min 40** | Provider reports completed payments missing in restored FIN01. | Finance Manager suspends final receipts; initiates dual-checked manual reconciliation via payment gateway logs. |

---

## Task 6 — Governance and Performance Program

### Standard Alignment
* **NIST SP 800-34 Rev. 1:** 7-step contingency planning process fully mapped across policy, BIA, preventive controls, recovery strategies, plan development, testing, and maintenance.
* **ISO 22301:2019 / Amd 1:2024:** Fully aligned with BCMS context, leadership, operation, performance evaluation, and climate change risk factors (flood exposure analysis).

### Key Performance Indicators (KPIs)

$$\text{Recovery Performance (\%)} = \left( \frac{\text{RTO-Compliant Technical Restorations}}{\text{Total Tested Functions}} \right) \times 100$$

* **Target:** $\ge 90\%$ overall.
* **Baseline Drill Result:** $4/5 = 80\%$ (F1 breached).

$$\text{RPO Compliance (\%)} = \left( \frac{\text{Compliant Verified Dependency Points}}{\text{Assessed Dependency Points}} \right) \times 100$$

* **Target:** $100\%$ for F1/F2; $\ge 95\%$ overall.
* **Baseline Drill Result:** $4/10 = 40\%$ (Model age comparison).

### Proposed Corrective Action Plan (CAP)

| ID | Action Item | Priority | Target Timeline | Verification Evidence |
| :--- | :--- | :--- | :--- | :--- |
| **CA01** | Confirm 5-day alternate site occupancy agreement. | P1 | Day +7 | Signed 120-hour facility SLA. |
| **CA02** | Resolve 40-candidate workstation deficit. | P1 | Day +7 | 40 tested seats or approved remote exam policy. |
| **CA03** | Validate DB01 contiguous chain & fallback restores. | P1 | Day +14 | Verified backup hashes and test restore logs. |
| **CA04** | Enforce separation of backup admin credentials & MFA. | P1 | Day +14 | Audited IAM policy and independent access logs. |
| **CA05** | Establish payment gateway auto-reconciliation script. | P1 | Day +14 | 100% test reconciliation log signed by Finance. |
| **CA06** | Re-run technical recovery drill with two-tech model. | P2 | Day +21 | Timed execution logs and signed review. |
| **CA07** | Executive Sponsor re-approval of residual risks. | P2 | Day +30 | Signed risk acceptance form. |
| **CA08** | Conduct full multi-role tabletop exercise. | P2 | Day +30 | Exercise minutes, log, and updated BCP. |

---

## BCDR Program Maturity Roadmap

```
Current State: Level 2 (Developing)              Target State: Level 3 (Defined)
+------------------------------------+           +------------------------------------+
| • Partial backup automation        |           | • Approved policies & roles        |
| • Modelled runbooks                | ------>   | • Segregated backup IAM / MFA      |
| • Workstation shortages unresolved |  12 Mos   | • Validated DB01/AUTH01 restores   |
| • Shared backup credentials        |           | • Quarterly drills & formal KPIs   |
+------------------------------------+           +------------------------------------+
```

---

## References

1. **ICDFA** (n.d.-a). *GRC205 Incident Management and Business Continuity: Business Continuity and Disaster Recovery Assignment*, Week 21, pp. 1–8.
2. **ICDFA** (n.d.-b). *Business Continuity and Disaster Recovery*, GRC205 Week 21, teaching slides 1–15.
3. **NIST** (2010). *Contingency Planning Guide for Federal Information Systems*. NIST Special Publication 800-34, Revision 1. [https://doi.org/10.6028/NIST.SP.800-34r1](https://doi.org/10.6028/NIST.SP.800-34r1)
4. **ISO** (2019). *ISO 22301:2019 — Security and resilience: Business continuity management systems — Requirements*. [https://www.iso.org/standard/75106.html](https://www.iso.org/standard/75106.html)
5. **ISO** (2024). *ISO 22301:2019/Amd 1:2024 — Climate action changes*.

---

### AI Assistance Acknowledgement
AI assistance was utilized for initial structural drafting, calculation verification, mathematical notation formatting, and markdown table organization. All analytical conclusions, compliance evaluations, and risk determinations remain the responsibility of the author.

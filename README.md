INTERNATIONAL CYBERSECURITY AND DIGITAL FORENSICS ACADEMY

Business Continuity and Disaster Recovery
GRC205 — Incident Management and Business Continuity
Individual Assessment: Northbridge Skills Institute


Student information	Details
Student	Ibrahim Abdullahi
Registration number	2025/GCR/12720
Official email	gcr2512720@students.icdfa.edu.ng

Program	GRC Engineering (CGRCE)
School	School of Cyber Risk, Governance and Compliance
Cohort	Batch B2025
Academic session	2026
Level / year	Level 1 / Year 1
Course	GRC105 — Incident Management and Business Continuity
Assignment	Business Continuity and Disaster Recovery



 Scope, Method and Assumptions
This report evaluates business continuity and disaster recovery arrangements for Northbridge Skills Institute, a fictional institution with 1,800 learners and 90 staff. The scenario begins at 08:00 WAT on Monday (Day 0), when flooding and a power outage render the main campus and locally hosted services unavailable. The initial closure estimate is 72 hours. Microsoft 365 email remains accessible via mobile internet, while local applications depend on the recovery network and AUTH01. Recovery activities are limited to two technicians. Of the 120 candidates scheduled for an 11:00 examination, 40 require institution-provided workstations, but only 25 are available at alternative premises from 10:00. The scenario confirms flooding as the cause of disruption, with no confirmed cyberattack (ICDFA, n.d.-a, pp. 1–4).
The analysis uses the scenario’s stated costs, backup checkpoints, system dependencies, recovery durations and annual budget limit of NGN 3,000,000 as its planning baseline. These inputs are treated as supplied parameters rather than independently verified operational data. Recommended recovery objectives, control measures, responsibilities and governance arrangements are proposals subject to institutional review and approval. The report distinguishes between technical recovery, restoration of minimum essential services and the formal acceptance of normal operations. Its approach is informed by NIST SP 800-34 and ISO 22301, but it does not represent a formal certification assessment or evidence of an actual recovery exercise (NIST, 2010; ISO, 2019).
Task 1 — Business Impact Analysis
Business priority follows time-sensitive consequences, learner welfare and integrity, not only the hourly rate. F1 is first because a failed 11:00 examination incurs immediate educational harm and a one-off cost. F2 and F3 follow because fee confirmation closes at 16:00 and admissions at 18:00 on Day 0. F4 payroll bank instructions are due 12:00 on Day 1; F5 records have a 48-hour internal commitment. Payroll and sensitive record cases can be escalated despite their lower default ranking (ICDFA, n.d.-a, pp. 1–4; ICDFA, n.d.-b, slide 5).
Priority / function; owner	Affected users, dependency and time constraint	Minimum acceptable service and control
1. F1 Teaching/assessment; Academic Director	120 exam candidates; broader learners/tutors. Network, AUTH01, DB01, LMS01; 11:00 exam; NGN 60,000/h.	Accessible authorized delivery or equitable rescheduling, candidate authentication, invigilation, signed attendance, exam-integrity approval. Only 25 of 40 Centre workstations supplied.
2. F2 Fees/finance; Finance Manager	Payers/finance staff. Network, AUTH01, DB01, FIN01 and external provider; 16:00 fee confirmation; NGN 40,000/h.	Provider-verified provisional acknowledgement, unique transaction IDs, dual review and eventual reconciliation; do not present provisional entries as posted balances.
3. F3 Admissions; Registrar	Applicants/registrars. Network, AUTH01, DB01, REG01; 18:00 close; NGN 20,000/h.	Time-stamped restricted intake with case references, authorized cutoff/appeal handling, duplicate and eligibility verification before later import.
4. F4 Payroll; HR Manager	Up to 90 staff. Network, AUTH01, DB01, HR01, bank; Day 1 12:00 submission; NGN 10,000/h.	Last verified payroll plus approved amendments, independent HR/Finance sign-off, bank acknowledgement and duplicate prevention controls.
5. F5 Certificates/records; Records Manager	Learners/alumni/staff. Network, AUTH01, FS01; 48-hour commitment; NGN 5,000/h.	Restricted request queue; issue authentic records only against independent verified sources and Records Manager authority.

People's requirements include service owners, invigilators, learner accessibility support, independent finance and payroll approvers, the two designated technicians and trained records staff. Premises must have safe occupancy, reliable power/connectivity, accessible assessment arrangements, and restricted record space. Suppliers include alternative-site operators, the payment provider, bank, connectivity operators, and offsite backup custodians. Necessary information includes approved rosters, candidate instructions, transaction references, payroll mandates, backup catalogues, and protected temporary registers. Their detailed availability is unverified.
Function	8-hour worked cost (NGN)	24-hour worked cost (NGN)
F1	60,000 × 8 + 120,000 = 600,000	60,000 × 24 + 120,000 = 1,560,000
F2	40,000 × 8 = 320,000	40,000 × 24 = 960,000
F3	20,000 × 8 = 160,000	20,000 × 24 = 480,000
F4	10,000 × 8 = 80,000	10,000 × 24 = 240,000
F5	5,000 × 8 = 40,000	5,000 × 24 = 120,000
TOTAL	135,000 × 8 + 120,000 = 1,200,000	135,000 × 24 + 120,000 = 3,360,000

The five independent rates sum to NGN 135,000 per hour. Both hypothetical periods include the NGN 120,000 examination-rescheduling charge exactly once because no acceptable assessment is assumed by 11:00. Rates apply only to the first 24 hours, so extrapolation to 72 hours is invalid. These simplified no-mitigation estimates exclude uncertain avoided costs and the non-financial consequences of learner exclusion, reputation, privacy, evidence of integrity and payroll error. They are not observing losses.
Principal dependencies are concentrated in DB01 (F1–F4), AUTH01 (all five), and the recovery network. A third major risk is that 40 candidates need center devices, but only 25 workstations exist, leaving a simultaneous deficit of 15. A fourth is a two-technician competition for indivisible recovery actions. Consequently, business coordination must operate temporary services in parallel while technicians obey the prerequisite sequence; Microsoft 365's email does not replace AUTH01.
Task 2 — Recovery Objectives and Backup Design
RTO targets a declared minimum acceptable service following disruption; RPO limits the age of recoverable data; MTD defines the outer tolerable business interruption. Targets below are proposed—not institutional commitments or demonstrated capabilities. A rescheduled examination preserves administrative continuity but does not count as an examination delivered on time; it may still incur the stipulated charge (ICDFA, n.d.-b, slide 6).
Function	RTO / deadline	RPO	MTD / buffer	Owner acceptance gate
F1	2 h / 10:00	15 min	3 h / 1 h	Academic Director certifies secure accessible exam arrangements; if infeasible, authorized reschedule and RTO breach recorded.
F2	4 h / 12:00	30 min	8 h / 4 h	Finance accepts a provider-confirmed provisional register with dual review.
F3	6 h / 14:00	1 h	10 h / 4 h	Registrar accepts a timestamped, privacy-controlled admissions channel.
F4	20 h / Day 1 04:00	4 h	28 h / 8 h	HR and Finance dual-authorize verified bank file.
F5	24 h / Day 1 08:00	24 h	48 h / 24 h	Records Manager accepts secure queue and authenticated record checks.



Checkpoint	At 08:00 Day 0	Potential gap
B01 DB01 full, 23:00 Day −1	9 h old	Base image alone cannot meet transactional RPOs.
B02 DB01 incremental through 07:00 Day 0	1 h old	Latest recoverable point if full contiguous chain passes.
B03 AUTH01 snapshot, 00:00 Day 0	8 h old	Identity changes after midnight may be absent.
B04 FS01 full, 23:00 Day −1	9 h old	File/permission changes since checkpoint may be lost.
Disconnected full, 17:00 Day −3	63 h old	Fallback, not ordinary compliant recovery.

The 63-hour age is 7 hours to midnight on Day −3, plus two full 24-hour days and eight hours on Day 0. In the stipulated successful baseline, DB01's age is one hour: F1 exceeds its 15-minute target by 45 minutes, and F2 exceeds 30 minutes by 30 minutes. F3 is at its one-hour boundary; F4 meets its four-hour transaction-data target. AUTH01 is eight hours old and exceeds a conservative application-wide RPO for F1–F4; FS01 and AUTH01 remain inside F5’s 24-hour age allowance. Passing checkpoint-age arithmetic does not establish integrity or successful application recovery.
To address the gap, propose weekly application-consistent DB01 full backups, daily differential copies and 15-minute transaction-log or incremental capture, coordinated with recoverable application versions. Protect AUTH01 configuration and state after changes and at intervals designed to support its approved objective; use weekly FS01 full and daily incremental/version captures. Retain local fast-restore copies, encrypted geographically separate copies, and an independently administered immutable or disconnected copy. Proposed operational retention is seven days locally, 35 days offsite and monthly protected archives for 12 months, subject to legal retention, capacity, supplier verification and cost approval (ICDFA, n.d.-b, slide 8).
The precise DB01 restoration chain is B01 full at 23:00 followed by every required, chronological B02 incremental up to 07:00; individual increment identifiers are not supplied and must not be fabricated. Review signed manifests and hashes, encrypted key access, configuration compatibility, privileged access and post-restore sample transactions. Production and network-backup administration presently share one identity; the offsite provider’s access independence is undocumented. Segregate credentials and MFA, test offline access without production identity, and preserve logs. A live replica can propagate corruption and is not a substitute for point-in-time protected backups. If any chain element fails, quarantine it, select the most recent fully verified alternative, recalculate RPO impact and obtain business-owner approval. Provider payment references can help reconcile financial entries, but missing exam answers, unaudited identity changes, and unknown edits cannot be assumed to be reconstructed (NIST, 2010).
Task 3 — Strategy and Budget
The annual budget ceiling is NGN 3,000,000. Each package covers five services and shared infrastructure and requires NGN 400,000 independent protected backups plus NGN 200,000 training/testing. Recovery windows are estimates for the first critical service, not validated completion times for all business functions (ICDFA, n.d.-a, p. 3).
Package	Base + backups + tests (NGN)	Total / headroom (NGN)	Estimated first service / loss	Capability and limitation
Cold	600,000 + 400,000 + 200,000	1,200,000 / 1,800,000	24–48 h / up to 24 h	Unacceptable for short F1/F2 objectives; staff must build and restore the environment.
Warm	1,500,000 + 400,000 + 200,000	2,100,000 / 900,000	3–5 h / 1–6 h	Feasible provisional foundation; cannot guarantee F1/F2 RTO/RPO; rely on approved workarounds.
Hot	2,400,000 + 400,000 + 200,000	3,000,000 / 0	About 1 h / up to 15 min	Potentially stronger objectives; consume entire ceiling and still needs tested failover/backup/device support.

Recommend the warm site provisionally: it leaves NGN 900,000 headroom, avoids cold-site delays, and can support controlled temporary workflows. Nevertheless, it cannot satisfy F1’s two-hour technical restoration objective in the supplied drill or guarantee 15/30-minute F1/F2 RPOs. Two technicians, provider access arrangements and independent geographically/power-diverse premises must be validated. The 15-device examination shortfall requires supplier-confirmed additional devices, an integrity-preserving approved alternative, or fair rescheduling. The Executive Sponsor must expressly accept residual exam, data-loss, staffing, corruption and supplier risks with Academic/Finance owner endorsement; if these are unacceptable, reassess hot-site procurement or revise targets only following an approved BIA review.
The NGN 2,100,000 annual warm-plan cost lies between the hypothetical eight-hour loss (NGN 1,200,000) and 24-hour loss (NGN 3,360,000). The difference between the latter and the plan is NGN 1,260,000; this is not an annual net benefit. One scenario supply neither outage frequency/probability nor the loss avoided by actual recovery, so annual ROI cannot be calculated defensibly. Management must obtain outage history, tested function-specific restoration and data points, supplier service-level evidence, setup and connectivity quotations, alternate-site flood exposure, exam equipment cost and security assurance before spending or accepting promised recovery times.
Task 4 — Coordinated Continuity and Disaster Recovery Plan
The Executive Sponsor/Institute Director is proposed to include Incident Commander and authorize activation, residual risks, exceptional spending, rescheduling and safe return. The Deputy Director acts only on recorded delegation. The BC/DR Coordinator maintains the decision log, priorities, and situation report. Facilities controls access and safe premises; the DR Lead allocates two technicians; service owners approve business workarounds and acceptance. Communications distribute approved messages; Information Security/IR investigates credible malicious-activity indicators without assuming the flood is an attack. Activate where unsafe premises or critical systems threaten deadlines; a signed decision should be proposed at 08:00. Issue updates hourly until the examination decision, then four-hourly Day 0 and twice daily thereafter, with immediate escalation for objective breach or compromised backup.
Activity	Responsible (R)	Accountable (A)	Consulted / informed
Plan activation	BC Coordinator	Incident Commander	Facilities, DR, Academic; all staff informed
Temporary exam/reschedule	Academic Director, BC	Incident Commander	Facilities, security; learners informed
Backup validation	DR technicians	DR Led	Security, business owners; BC informed
Infrastructure and application restore	DR technicians	DR Led	Security, owners; Incident Commander informed
Communications	Communications Lead	Incident Commander	Academic, Facilities, Security; stakeholders informed
Financial reconciliation	Finance staff	Finance Manager	DR, payment provider; Incident Commander informed
Payroll instructions	HR and Finance staff	HR Manager	Bank, security; Incident Commander informed
Site clearance	Facilities staff	Facilities Lead	Qualified utilities/safety staff; Incident Commander informed
Return to primary site	BC, Facilities, DR, owners	Incident Commander	Security, Communications; users informed

For F1, an authorized secure BYOD and center arrangement must verify identity, accessibility, invigilation and assessment of integrity; 80 candidates have their own devices while 40 need center workstations, and only 25 are supplied. Fifteen additional tested devices or formally approved fair alternative scheduling is needed; neither is assumed available. F2 uses numbered provider-confirmed provisional payment entries reviewed by two staff members. F3 accepts restricted time-stamped admissions forms with cutoff and appeal rules. F4 prepares bank instructions only from verified payroll and authorized changes, with HR/Finance approvals. F5 uses a restricted request to queue and issues certificates only when authentic source records can be verified. Every interim record needs a unique reference, restricted storage, owner approval and reconciled import; finance and payroll need explicit duplicate-prevention checks.
DR step / owner	Prerequisite and acceptance test	If unsuccessful
1 Network / Technician	Safe alternate site; connectivity, routing and security checks (30 min).	Use an approved alternative link; log delay.
2 AUTH01 / Technician	Network; test trusted accounts and permissions (30 min).	Isolate questionable identity state; restore verified copy.
3 Backup/security checks / DR Lead	AUTH01; Provide integrity/independent access and B01+B02 chain (30 min).	Quarantine failures; engage IR if suspicious; re-evaluate RPO.
4 DB01 / Technician	Checks passed; full plus ordered increments, data consistency (90 min).	Restore earlier verified point; record business impact.
5 FS01 / Technician	Checks and AUTH01; permissions and record integrity (60 min).	Hold certificate issuance; choose approved fallback.
6 LMS/FIN/REG/HR / technicians	DB01; individual 45/30/30/45-minute actions; representative application tests.	Do not open unvalidated service; correct or roll back.
7 Acceptance/cutover / service owners + Commander	Owners confirm usable controls/data, exceptions, accessible operations and approved cutover.	Continue manual minimum service; roll back to last accepted state.

Primary communication uses approved Microsoft 365 email over mobile access, with a verified voice/SMS call tree as fallback if tested. Learners receive exam and safety instructions before 11:00; staff receive site/shift notices; executives receive risk and recovery reporting; suppliers receive facility/restore requests; bank/provider communications use authenticated channels. Legal/IR advice determines whether statutory notification is required to flood alone does not establish a reportable cyber incident. Never send sensitive learners or payroll details over unofficial channels.
Initial learner notice (proposed; not issued)
Dear Northbridge learners,
Following flooding and a power failure at our main site at 08:00 WAT today, the campus is temporarily inaccessible. Please do not travel to or enter the affected premises until an official clearance notice is issued.
Teaching and assessment arrangements are being reviewed. Learners scheduled for the 11:00 examination should check their official Microsoft 365 email and approved institute announcement channel for individual confirmation of the examination arrangements. Do not assume that the examination has moved online or that your scheduled time has changed until you receive an approved instruction.
We are assessing accessible alternative facilities and arrangements for learners who require institution-provided workstations. No learner should be disadvantaged by the current equipment shortfall. Please do not submit examination answers, identity documents, or payment details through unofficial links.
Fee payments made through our existing provider remain available; receipt updates may be delayed while records are reconciled. Our learner support team will provide updates and assistance through established contact channels.
Thank you for your patience and cooperation.
Northbridge Skills Institute — Authorized Communications Office
Returning to the primary site requires qualified Facilities electrical/flood clearance, secure rebuilding and testing of on-site systems, protected transfer and reconciliation of interim records, independent business-owner acceptance for F1–F5 and authorized staged cutback with a rollback point. Only then does the Incident Commander sign operational closure. The initial 72-hour estimate is not a safety clearance. Preserve change logs, exceptions and final communications (ICDFA, n.d.-b, slides 10, 12 and 14).
Task 5 — Recovery Schedule and Simulated Tabletop
The following is a MODELLED baseline, not a live drill. Each action occupies one technician for its entire duration; it cannot be split. Network, AUTH01 and security checks are sequential; DB01 and FS01 can execute concurrently after checks. B01–B04 are assumed to pass integrity checks only for this baseline. Durations already include local technical validation (ICDFA, n.d.-a, pp. 3–4, 7).
Action	Technician	Start	Finish	Prerequisite
Network (30 min)	T1	08:00	08:30	None
AUTH01 (30 min)	T1	08:30	09:00	Network
Security/backup checks (30 min)	T1	09:00	09:30	AUTH01
DB01 (90 min)	T1	09:30	11:00	Checks
FS01 (60 min)	T2	09:30	10:30	AUTH01 and checks
LMS01 (45 min)	T1	11:00	11:45	DB01
FIN01 (30 min)	T2	11:00	11:30	DB01
HR01 (45 min)	T2	11:30	12:15	DB01
REG01 (30 min)	T1	11:45	12:15	DB01

Assessment critical path = 30 + 30 + 30 + 90 + 45 = 225 minutes from 08:00, so the earliest LMS01 finish is 11:45. Once DB01 completes at 11:00, four remaining applications require 45 + 30 + 45 = 150 technician-minutes; two technicians provide a theoretical 75-minute minimum, achieved by the schedule at 12:15. FS01 finishes separately at 10:30. There is no overlapping technician assignment; all five applications/files complete technically by 12:15 (elapsed 4 hours 15 minutes). Owner acceptance is not timed and cannot be assumed.
Function	Technical finish / elapsed	RTO / MTD result	Checkpoint against RPO
F1	11:45 / 3h45	RTO 2h missed 1h45; MTD 3h missed 45m	DB01 1h >15m by 45m; AUTH01 8h >15m
F2	11:30 / 3h30	4h RTO met; 8h MTD met	DB01 1h >30m by 30m; AUTH01 8h >30m
F3	12:15 / 4h15	6h RTO met; 10h MTD met	DB01 1h meets 1h; AUTH01 8h >1h
F4	12:15 / 4h15	20h RTO met; 28h MTD met	DB01 1h meets 4h; AUTH01 8h >4h
F5	10:30 / 2h30	24h RTO met; 48h MTD met	FS01 9h and AUTH01 8h meet 24h

Despite restored technology, the 11:00 examination needs a certified accessible continuity solution; FIN01 requires reconciliation before confirmed fee receipts; admissions require time-stamped cutoff evidence; HR01 requires controlled payroll approval and bank acknowledgment; and FS01 requires authenticated certificate source records. RTO passes in this table mean technical readiness only, not verified business resumption.
Separate 45-minute tabletop: simulated inject/decision log
Exercise minute / inject	Simulated decision and owner	Revised action and effect
10 — Closure extended from 72 hours to five days	Incident Commander authorizes extended continuity; Facilities confirm longer closure.	BC and Facilities seek 120-hour alternate-site coverage, staff Rota and revised learner updates; extra supplier cost/risk, no baseline schedule change.
20 — Available workstations fall from 25 to 15	Academic Director escalates exam fairness; Commander approves revised service decision.	40 − 15 = 25-device deficit; seek 25 tested accessible devices or approved equitable rescheduling; exam remains at risk.
30 — DB01 incremental fails integrity; unexpected backup-admin login	DR Led rejects untrusted chain; IR Lead preserves evidence and investigates; Commander escalates.	Find contiguous verified points; possibly 23:00 full (9h) or disconnected Day −3 (63h) only after risk acceptance; DB01-dependent finish and RPO become unknown.
40 — Provider confirms successful payments missing in restored finance	Finance Manager suspends final receipts pending dual-checked reconciliation.	Match provider/bank IDs and temporary ledger against DB01; prevent duplicate credit; FIN01 not accepted until evidence reconciled.

At simulated minute 45, the coordinator reports the five-day closure, device deficit, suspect backup identity event and payment gaps. The Commander hypothetically directs continued controlled continuity and blocks promotion of unverified DB01 data. These are not observed decisions by real staff. The baseline 11:45 LMS01 and 12:15 final completion times cannot be transferred to the stress scenario: the invalid incremental and undisclosed restore durations make revised technical completion unknowable.
Corrective action	Priority / owner	Target after exercise	Completion evidence
CA01 Confirm five-day alternate occupancy and support	P1 / Facilities	Day +7	Signed 120-hour accessible site/supplier checklist
CA02 Cover 40 exam-device users under 15-machine stress	P1 / Academic Director	Day +7	40 tested seats or approved fair alternative with integrity trial
CA03 Validate DB01 contiguous chain, fallback and isolated restore	P1 / DR Lead	Day +14	Verified hashes, restore time and recoverable checkpoint
CA04 Separate backup administration and test supplier independence	P1 / Security Lead	Day +14	Distinct tested access, audit and suspicious-login alert
CA05 Test missing/duplicate financial payment reconciliation	P1 / Finance Manager	Day +14	100% simulated IDs reconciled or exception-coded, signed dual review
CA06 Re-run two-tech fallback schedule	P2 / BC Coordinator	Day +21	Witnessed schedule and objective breach log
CA07 Reapprove targets, risk and warm supplier evidence	P2 / Executive Sponsor	Day +30	Signed risk/contract and objective decision
CA08 Repeat communication and accessible-facility tabletop	P2 / BC Coordinator	Day +30	Documented 45-minute log and closure review

All eight actions are PROPOSED, and zero real-world closures are evidenced. Target dates are relative to simulated exercise end, not calendar promises (ICDFA, n.d.-b, slide 11).
Task 6 — Governance and Performance Measures
The Executive Sponsor approves policy, budget, exceptions and annual reviews; the BC/DR Coordinator owns controlled plan versions, the exercise registers and management reporting. Service owners approve minimum service, the DR Lead validates technical performance, Facilities owns premises safety, Security reviews protected backup access, and HR manages responder competence. Store a controlled master, encrypted/offline emergency role copies, a recipient/access register and change log. Review at least annually and after flood-risk, premises, supplier, system, workforce, examination-timetable, privacy or failed-restore changes. Do not publish live contact lists, credentials or learner data on a public repository.
The proposed 12-month program includes daily backup monitoring with weekly exception review; monthly isolated DB01 point-in-time chain restores; quarterly AUTH01/FS01 restores and 45-minute multi-role tabletops; semiannual two-tech runbook and service-acceptance walkthroughs; annual alternate-site/supplier review and management approval; and onboarding/role-change training. Collect signed timestamps, recoverable points, access-independence evidence, owner acceptance and tracked remediation. A simulated schedule does not satisfy actual test completion.
Framework	Coursework alignment
NIST 1 — Policy	Task 4 activation/authority, Task 6 ownership and approval
NIST 2 — BIA	Task 1 functions, costs, deadlines and dependencies
NIST 3 — Preventive controls	Task 2 independent protected backups and flood/power prevention
NIST 4 — Strategy	Task 3 priced alternatives and residual-risk decision
NIST 5 — Contingency plan	Task 4 runbook, temporary workflows and cutback
NIST 6 — Tests/training	Task 5 model/tabletop and Task 6 calendar
NIST 7 — Maintenance	Task 6 triggers and controlled versions
ISO 22301 context/leadership	Flood, interested parties, sponsor roles (clauses 4–5)
ISO planning/support	Objectives, resources, communication and competence (clauses 6–7)
ISO operation	BIA, continuity procedures, recovery/exercises (clause 8)
ISO performance/improvement	Metrics, management review, corrective actions (clauses 9–10)

The NIST mapping follows SP 800-34 Rev. 1 and the teaching deck slide 4; ISO alignment is a high-level educational interpretation of ISO 22301 themes on slide 9, not certification. ISO 22301:2019 Amendment 1:2024 requires considering climate issues in context: Northbridge should assess local floodplain exposure, drainage, rainfall extremes, common electrical substations and alternate-site hazard correlation before approving geographic separation (ISO, 2024).
KPI / measurement	Target; reporting / accountable	Evidence status
Recovery performance = 100 × RTO-compliant technical restorations / tested functions; report accepted business service separately.	≥90% overall; critical F1 either 100% or signed exception. Each test / DR Lead.	Model only: 4/5 = 80%, not a live test.
RPO checkpoint compliance = 100 × compliant verified function-dependency points / assessed points.	100% F1/F2 critical; ≥95%. Monthly/quarterly / DR + Security.	Model age comparison: 4/10 = 40%; not successful restore evidence.
Restore-test coverage = 100 × critical assets restore-tested / critical assets inventoried.	100% annually; quarterly / BC Coordinator.	Not measured in real operations.
On-time action closure = 100 × due actions evidenced closed on time / all actions due.	≥90%; zero P1 overdue without exception. Monthly / BC Coordinator.	Eight simulated proposed actions; no real closure reported.
Training completion = 100 × trained assessed responders / assigned responders.	≥95%; 100% command decisionmakers. Quarterly / HR.	Not measured; real roster absent.
Plan currency = 100 × in-date and trigger-reviewed plans / approved plans.	100%. Quarterly / BC Coordinator.	Not measured; plan is an academic proposal.

Using the teaching slide 13 model (Initial, Developing, Defined, Managed, Optimizing), the fictional case supports an indicative Level 2 (Developing) planning position rather than a verified maturity score: some backups and modelled runbook activity exist, but independent access, tested restores and sufficient examination devices remain unproven. A credible 12-month goal is Level 3 (Defined): Months 1–3 approve roles, objectives and supplier risks; Months 4–6 segregate backup access and verify DB01/AUTH01/FS01 restores; Months 7–9 perform documented drills and training; Months 10–12 demonstrate recurring measurement, closure evidence and signed management review. If exam delivery or protected restores remain unsupported, retain Level 2 rather than declare achievement.
Cross-task interpretation and assurance limits
For assessment purposes, business urgency must be distinguished from restoration sequences. The first activity required by every local function is the recovery network; AUTH01 then enables controlled authentication, and a security-and-backup validation step precedes data restore. Although teaching has first business priority, an attempt to start LMS01 before DB01 has finished is technically infeasible. Similarly, starting FS01 while the identity restoration is still underway would breach the prerequisite constraint. Owners should therefore work on learners, safe premises, accessible equipment, and temporary recording before their applications are ready. The program must also check that “available” means accessible to authorized users, reconciled sufficiently for the stated minimum service, and backed by a signed owner's decision. The technical baseline excludes that final acceptance duration, so the scheduled times must not be presented as proven recovery service levels.
Recovery objective buffers are intentionally asymmetric. F1 has only one hour between the proposed two-hour business RTO and the 11:00 intolerable examination decision, reflecting the exceptional fixed start. F2 and F3 have four hours before their respective confirmation and application deadlines; these hours are reserved for testing, correcting and communicating temporary procedures. Payroll provides eight hours between its proposed RTO and bank deadline, whereas certificates have a 24-hour buffer. These intervals are planning safeguards rather than idle time, and some do not guarantee success: F1 lacks fifteen institution-provided devices, and the warm site cannot deliver LMS01 before 11:45 in the baseline. An executive cannot simply declare F1 compliant by recording a rescheduling notice; the original examination delivery target has still been missed.
The backup architecture must maintain a reliable distinction between a backup job, an accessible copy, and a recoverable service. An apparently successful database backup can omit a required incremental or store encrypted copies behind the same credentials that were lost during a disaster. In such circumstances, offsite geography alone provides insufficient assurance. For DB01, restoration requires B01 and every required B02 increment up to the selected point; a single unverified segment breaks confidence in the later chain. Accordingly, the test evidence must include source identity, timestamp, chain continuity, hash or consistency result, successful isolation and business data examples. Independent administrator access is a resilience control as well as a security control; a suspicious login in the exercise warrants investigation without permitting the author to infer confirmed malicious compromise.
The recommended warm-site option is a decision under constrained information, not an unconditional optimum. All quoted packages fit within the NGN three-million limit. The hot package is more promising for the strict F1 time and data targets but has no monetary contingency for additional workstations, supplier onboarding or unexpected licensing; the cold option sacrifices time-critical services despite its lower fixed cost. Warm preserves NGN 900,000 headroom, which is an unallocated planning margin rather than a verified procurement budget. Management should request total cost and geographic-separation evidence, define acceptance demonstrations for each application, and secure explicit risk approval. If the supplier cannot prove its recoverable data point or two-technician feasibility, the selection must return to the executive decision forum.
The learner and finance workarounds need equally strong evidential discipline. An examination administered across a physical room and learners’ own devices requires confirmation that the platform, accessibility of accommodations, invigilation arrangements and question security are equivalent. Separately scheduled groups could obtain unfair access to questions, so staggering must not be used without academic sign-off. For fees, a provider's settlement proves that the provider recorded a transaction, not that a restored FIN01 wallet balance is correct. A duplicate posted transaction may create a second apparent payment; an omitted one may unfairly exclude a learner. Matching unique IDs, bank/provider exports and interim logs under independent review provide a traceable route from temporary continuity to accepted normal processing. Similar controls apply to admissions timestamps and payroll amendment authorization.
The tabletop is intentionally a stressor rather than a second timed restoration dataset. At minute ten the five-day closure changes accommodation assumptions but not the specified durations of network or database restoration. At minute twenty the shortage grows to 25 Centre devices, potentially invalidating an already fragile examination plan. At minute thirty the database recovery point itself becomes unreliable; because the corrupt incremental and fallback restore time are not given, neither the new data-loss exposure nor the service finish time can be calculated responsibly. Minute forty shows that even a functioning finance application can carry incomplete business records. These distinctions make the exercise useful: participants would have to revise communications, decision authority, supplier engagement and objective reporting instead of presenting unsupported numerical precision.
Governance must convert each proposed corrective action into testable evidence. CA03, for example, is not closed merely because a backup policy now demands integrity validation: the DR Lead must demonstrate an isolated complete restore and record the achieved point. CA04 requires an independently accessible supplier to copy and separate privileged credentials, not a statement that offsite storage exists. Training completion should be measured against a real roster, while restoration coverage needs an approved system of inventory. Dashboard denominators must be retained with each report to prevent misleading percentages. The maturity objective of Level 3 is defensible only if the documented plans become approved, distributed, rehearsed and consistently followed, with evidence that material exceptions are escalated and resolved. This prevents academic drafting from being misrepresented as operational resilience.
Conclusion
The BIA makes assessment of integrity and deadlines central to continuity decisions. An NGN 2.1 million warm-site strategy is affordable but cannot alone meet the examination deadline or stringent F1/F2 data objectives. An appropriate response combines protected backups, tested dependencies, accessible temporary services, independent business acceptance, transparent exception handling and disciplined governance. The 45-minute tabletop exposes exactly why supplier assurances and backup job success must be verified before recovery capability is claimed. Every result in this report is either a supplied exercise estimate, a derived model, or a proposed/simulated decision—not evidence of an actual incident response.







References
ICDFA (n.d.-a). GRC205 Incident Management and Business Continuity: Business Continuity and Disaster Recovery Assignment, Week 21, pp. 1–8. Provided assessment brief.
ICDFA (n.d.-b). Business Continuity and Disaster Recovery, GRC205 Week 21, teaching slides 1–15. Provided teaching deck.
NIST (2010). Contingency Planning Guide for Federal Information Systems. NIST Special Publication 800-34, Revision 1. https://doi.org/10.6028/NIST.SP.800-34r1
ISO (2019). ISO 22301:2019 — Security and resilience: Business continuity management systems — Requirements. https://www.iso.org/standard/75106.html
ISO (2024). ISO 22301:2019/Amd 1:2024 — Climate action changes. Official ISO amendment overview.














AI assistance acknowledgement
AI assistance was used to support initial drafting, calculation checks, structured tables, and document formatting. The author is responsible for reviewing the evidence, correcting any inaccuracies, ensuring compliance with the course of AI policy, and defending the analytical decisions. No live testing, institutional approvals, or supplier confirmation are asserted.

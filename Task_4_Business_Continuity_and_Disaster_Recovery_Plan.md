# Task 4 --- Business Continuity and Disaster Recovery Plan

**Course:** GRC205 --- Business Continuity and Disaster Recovery\
**Assessment scenario:** Northbridge Skills Institute\
**Student:** Ibrahim Abdullahi\
**Registration number:** 2025/GCR/12720

> This file contains the relevant section of the submitted assignment,
> separated for easier review. Supplied scenario details, proposed
> controls, modelled results and caveats are retained as presented in
> the source document.

The Executive Sponsor/Institute Director is proposed to include Incident
Commander and authorize activation, residual risks, exceptional
spending, rescheduling and safe return. The Deputy Director acts only on
recorded delegation. The BC/DR Coordinator maintains the decision log,
priorities, and situation report. Facilities controls access and safe
premises; the DR Lead allocates two technicians; service owners approve
business workarounds and acceptance. Communications distribute approved
messages; Information Security/IR investigates credible
malicious-activity indicators without assuming the flood is an attack.
Activate where unsafe premises or critical systems threaten deadlines; a
signed decision should be proposed at 08:00. Issue updates hourly until
the examination decision, then four-hourly Day 0 and twice daily
thereafter, with immediate escalation for objective breach or
compromised backup.

  ------------------------------------------------------------------------
  Activity          Responsible (R)   Accountable (A)   Consulted /
                                                        informed
  ----------------- ----------------- ----------------- ------------------
  Plan activation   BC Coordinator    Incident          Facilities, DR,
                                      Commander         Academic; all
                                                        staff informed

  Temporary         Academic          Incident          Facilities,
  exam/reschedule   Director, BC      Commander         security; learners
                                                        informed

  Backup validation DR technicians    DR Led            Security, business
                                                        owners; BC
                                                        informed

  Infrastructure    DR technicians    DR Led            Security, owners;
  and application                                       Incident Commander
  restore                                               informed

  Communications    Communications    Incident          Academic,
                    Lead              Commander         Facilities,
                                                        Security;
                                                        stakeholders
                                                        informed

  Financial         Finance staff     Finance Manager   DR, payment
  reconciliation                                        provider; Incident
                                                        Commander informed

  Payroll           HR and Finance    HR Manager        Bank, security;
  instructions      staff                               Incident Commander
                                                        informed

  Site clearance    Facilities staff  Facilities Lead   Qualified
                                                        utilities/safety
                                                        staff; Incident
                                                        Commander informed

  Return to primary BC, Facilities,   Incident          Security,
  site              DR, owners        Commander         Communications;
                                                        users informed
  ------------------------------------------------------------------------

For F1, an authorized secure BYOD and center arrangement must verify
identity, accessibility, invigilation and assessment of integrity; 80
candidates have their own devices while 40 need center workstations, and
only 25 are supplied. Fifteen additional tested devices or formally
approved fair alternative scheduling is needed; neither is assumed
available. F2 uses numbered provider-confirmed provisional payment
entries reviewed by two staff members. F3 accepts restricted
time-stamped admissions forms with cutoff and appeal rules. F4 prepares
bank instructions only from verified payroll and authorized changes,
with HR/Finance approvals. F5 uses a restricted request to queue and
issues certificates only when authentic source records can be verified.
Every interim record needs a unique reference, restricted storage, owner
approval and reconciled import; finance and payroll need explicit
duplicate-prevention checks.

  -----------------------------------------------------------------------
  DR step / owner         Prerequisite and        If unsuccessful
                          acceptance test         
  ----------------------- ----------------------- -----------------------
  1 Network / Technician  Safe alternate site;    Use an approved
                          connectivity, routing   alternative link; log
                          and security checks (30 delay.
                          min).                   

  2 AUTH01 / Technician   Network; test trusted   Isolate questionable
                          accounts and            identity state; restore
                          permissions (30 min).   verified copy.

  3 Backup/security       AUTH01; Provide         Quarantine failures;
  checks / DR Lead        integrity/independent   engage IR if
                          access and B01+B02      suspicious; re-evaluate
                          chain (30 min).         RPO.

  4 DB01 / Technician     Checks passed; full     Restore earlier
                          plus ordered            verified point; record
                          increments, data        business impact.
                          consistency (90 min).   

  5 FS01 / Technician     Checks and AUTH01;      Hold certificate
                          permissions and record  issuance; choose
                          integrity (60 min).     approved fallback.

  6 LMS/FIN/REG/HR /      DB01; individual        Do not open unvalidated
  technicians             45/30/30/45-minute      service; correct or
                          actions; representative roll back.
                          application tests.      

  7 Acceptance/cutover /  Owners confirm usable   Continue manual minimum
  service owners +        controls/data,          service; roll back to
  Commander               exceptions, accessible  last accepted state.
                          operations and approved 
                          cutover.                
  -----------------------------------------------------------------------

Primary communication uses approved Microsoft 365 email over mobile
access, with a verified voice/SMS call tree as fallback if tested.
Learners receive exam and safety instructions before 11:00; staff
receive site/shift notices; executives receive risk and recovery
reporting; suppliers receive facility/restore requests; bank/provider
communications use authenticated channels. Legal/IR advice determines
whether statutory notification is required to flood alone does not
establish a reportable cyber incident. Never send sensitive learners or
payroll details over unofficial channels.

## Initial learner notice (proposed; not issued)

Dear Northbridge learners,

Following flooding and a power failure at our main site at 08:00 WAT
today, the campus is temporarily inaccessible. Please do not travel to
or enter the affected premises until an official clearance notice is
issued. Teaching and assessment arrangements are being reviewed.
Learners scheduled for the 11:00 examination should check their official
Microsoft 365 email and approved institute announcement channel for
individual confirmation of the examination arrangements. Do not assume
that the examination has moved online or that your scheduled time has
changed until you receive an approved instruction. We are assessing
accessible alternative facilities and arrangements for learners who
require institution-provided workstations. No learner should be
disadvantaged by the current equipment shortfall. Please do not submit
examination answers, identity documents, or payment details through
unofficial links. Fee payments made through our existing provider remain
available; receipt updates may be delayed while records are reconciled.
Our learner support team will provide updates and assistance through
established contact channels.

Thank you for your patience and cooperation. Northbridge Skills
Institute --- Authorized Communications Office

Returning to the primary site requires qualified Facilities
electrical/flood clearance, secure rebuilding and testing of on-site
systems, protected transfer and reconciliation of interim records,
independent business-owner acceptance for F1--F5 and authorized staged
cutback with a rollback point. Only then does the Incident Commander
sign operational closure. The initial 72-hour estimate is not a safety
clearance. Preserve change logs, exceptions and final communications
(ICDFA, n.d.-b, slides 10, 12 and 14).

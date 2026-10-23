# Task 5 --- Recovery Schedule and Exercise

**Course:** GRC205 --- Business Continuity and Disaster Recovery\
**Assessment scenario:** Northbridge Skills Institute\
**Student:** Ibrahim Abdullahi\
**Registration number:** 2025/GCR/12720

> This file contains the relevant section of the submitted assignment,
> separated for easier review. Supplied scenario details, proposed
> controls, modelled results and caveats are retained as presented in
> the source document.

The following is a MODELLED baseline, not a live drill. Each action
occupies one technician for its entire duration; it cannot be split.
Network, AUTH01 and security checks are sequential; DB01 and FS01 can
execute concurrently after checks. B01--B04 are assumed to pass
integrity checks only for this baseline. Durations already include local
technical validation (ICDFA, n.d.-a, pp. 3--4, 7).

  Action                            Technician   Start   Finish   Prerequisite
  --------------------------------- ------------ ------- -------- -------------------
  Network (30 min)                  T1           08:00   08:30    None
  AUTH01 (30 min)                   T1           08:30   09:00    Network
  Security/backup checks (30 min)   T1           09:00   09:30    AUTH01
  DB01 (90 min)                     T1           09:30   11:00    Checks
  FS01 (60 min)                     T2           09:30   10:30    AUTH01 and checks
  LMS01 (45 min)                    T1           11:00   11:45    DB01
  FIN01 (30 min)                    T2           11:00   11:30    DB01
  HR01 (45 min)                     T2           11:30   12:15    DB01
  REG01 (30 min)                    T1           11:45   12:15    DB01

Assessment critical path = 30 + 30 + 30 + 90 + 45 = 225 minutes from
08:00, so the earliest LMS01 finish is 11:45. Once DB01 completes at
11:00, four remaining applications require 45 + 30 + 45 = 150
technician-minutes; two technicians provide a theoretical 75-minute
minimum, achieved by the schedule at 12:15. FS01 finishes separately at
10:30. There is no overlapping technician assignment; all five
applications/files complete technically by 12:15 (elapsed 4 hours 15
minutes). Owner acceptance is not timed and cannot be assumed.

  -----------------------------------------------------------------------
  Function          Technical finish  RTO / MTD result  Checkpoint
                    / elapsed                           against RPO
  ----------------- ----------------- ----------------- -----------------
  F1                11:45 / 3h45      RTO 2h missed     DB01 1h \>15m by
                                      1h45; MTD 3h      45m; AUTH01 8h
                                      missed 45m        \>15m

  F2                11:30 / 3h30      4h RTO met; 8h    DB01 1h \>30m by
                                      MTD met           30m; AUTH01 8h
                                                        \>30m

  F3                12:15 / 4h15      6h RTO met; 10h   DB01 1h meets 1h;
                                      MTD met           AUTH01 8h \>1h

  F4                12:15 / 4h15      20h RTO met; 28h  DB01 1h meets 4h;
                                      MTD met           AUTH01 8h \>4h

  F5                10:30 / 2h30      24h RTO met; 48h  FS01 9h and
                                      MTD met           AUTH01 8h meet
                                                        24h
  -----------------------------------------------------------------------

Despite restored technology, the 11:00 examination needs a certified
accessible continuity solution; FIN01 requires reconciliation before
confirmed fee receipts; admissions require time-stamped cutoff evidence;
HR01 requires controlled payroll approval and bank acknowledgment; and
FS01 requires authenticated certificate source records. RTO passes in
this table mean technical readiness only, not verified business
resumption.

## Separate 45-minute tabletop: simulated inject/decision log

  -----------------------------------------------------------------------
  Exercise minute /       Simulated decision and  Revised action and
  inject                  owner                   effect
  ----------------------- ----------------------- -----------------------
  10 --- Closure extended Incident Commander      BC and Facilities seek
  from 72 hours to five   authorizes extended     120-hour alternate-site
  days                    continuity; Facilities  coverage, staff Rota
                          confirm longer closure. and revised learner
                                                  updates; extra supplier
                                                  cost/risk, no baseline
                                                  schedule change.

  20 --- Available        Academic Director       40 − 15 = 25-device
  workstations fall from  escalates exam          deficit; seek 25 tested
  25 to 15                fairness; Commander     accessible devices or
                          approves revised        approved equitable
                          service decision.       rescheduling; exam
                                                  remains at risk.

  30 --- DB01 incremental DR Led rejects          Find contiguous
  fails integrity;        untrusted chain; IR     verified points;
  unexpected backup-admin Lead preserves evidence possibly 23:00 full
  login                   and investigates;       (9h) or disconnected
                          Commander escalates.    Day −3 (63h) only after
                                                  risk acceptance;
                                                  DB01-dependent finish
                                                  and RPO become unknown.

  40 --- Provider         Finance Manager         Match provider/bank IDs
  confirms successful     suspends final receipts and temporary ledger
  payments missing in     pending dual-checked    against DB01; prevent
  restored finance        reconciliation.         duplicate credit; FIN01
                                                  not accepted until
                                                  evidence reconciled.
  -----------------------------------------------------------------------

At simulated minute 45, the coordinator reports the five-day closure,
device deficit, suspect backup identity event and payment gaps. The
Commander hypothetically directs continued controlled continuity and
blocks promotion of unverified DB01 data. These are not observed
decisions by real staff. The baseline 11:45 LMS01 and 12:15 final
completion times cannot be transferred to the stress scenario: the
invalid incremental and undisclosed restore durations make revised
technical completion unknowable.

  ----------------------------------------------------------------------------
  Corrective action     Priority / owner  Target after      Completion
                                          exercise          evidence
  --------------------- ----------------- ----------------- ------------------
  CA01 Confirm five-day P1 / Facilities   Day +7            Signed 120-hour
  alternate occupancy                                       accessible
  and support                                               site/supplier
                                                            checklist

  CA02 Cover 40         P1 / Academic     Day +7            40 tested seats or
  exam-device users     Director                            approved fair
  under 15-machine                                          alternative with
  stress                                                    integrity trial

  CA03 Validate DB01    P1 / DR Lead      Day +14           Verified hashes,
  contiguous chain,                                         restore time and
  fallback and isolated                                     recoverable
  restore                                                   checkpoint

  CA04 Separate backup  P1 / Security     Day +14           Distinct tested
  administration and    Lead                                access, audit and
  test supplier                                             suspicious-login
  independence                                              alert

  CA05 Test             P1 / Finance      Day +14           100% simulated IDs
  missing/duplicate     Manager                             reconciled or
  financial payment                                         exception-coded,
  reconciliation                                            signed dual review

  CA06 Re-run two-tech  P2 / BC           Day +21           Witnessed schedule
  fallback schedule     Coordinator                         and objective
                                                            breach log

  CA07 Reapprove        P2 / Executive    Day +30           Signed
  targets, risk and     Sponsor                             risk/contract and
  warm supplier                                             objective decision
  evidence                                                  

  CA08 Repeat           P2 / BC           Day +30           Documented
  communication and     Coordinator                         45-minute log and
  accessible-facility                                       closure review
  tabletop                                                  
  ----------------------------------------------------------------------------

All eight actions are PROPOSED, and zero real-world closures are
evidenced. Target dates are relative to simulated exercise end, not
calendar promises (ICDFA, n.d.-b, slide 11).

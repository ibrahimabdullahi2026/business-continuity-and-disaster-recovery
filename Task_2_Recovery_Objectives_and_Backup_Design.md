# Task 2 --- Recovery Objectives and Backup Design

**Course:** GRC205 --- Business Continuity and Disaster Recovery\
**Assessment scenario:** Northbridge Skills Institute\
**Student:** Ibrahim Abdullahi\
**Registration number:** 2025/GCR/12720

> This file contains the relevant section of the submitted assignment,
> separated for easier review. Supplied scenario details, proposed
> controls, modelled results and caveats are retained as presented in
> the source document.

RTO targets a declared minimum acceptable service following disruption;
RPO limits the age of recoverable data; MTD defines the outer tolerable
business interruption. Targets below are proposed---not institutional
commitments or demonstrated capabilities. A rescheduled examination
preserves administrative continuity but does not count as an examination
delivered on time; it may still incur the stipulated charge (ICDFA,
n.d.-b, slide 6).

  --------------------------------------------------------------------------------
  Function       RTO / deadline RPO            MTD / buffer   Owner acceptance
                                                              gate
  -------------- -------------- -------------- -------------- --------------------
  F1             2 h / 10:00    15 min         3 h / 1 h      Academic Director
                                                              certifies secure
                                                              accessible exam
                                                              arrangements; if
                                                              infeasible,
                                                              authorized
                                                              reschedule and RTO
                                                              breach recorded.

  F2             4 h / 12:00    30 min         8 h / 4 h      Finance accepts a
                                                              provider-confirmed
                                                              provisional register
                                                              with dual review.

  F3             6 h / 14:00    1 h            10 h / 4 h     Registrar accepts a
                                                              timestamped,
                                                              privacy-controlled
                                                              admissions channel.

  F4             20 h / Day 1   4 h            28 h / 8 h     HR and Finance
                 04:00                                        dual-authorize
                                                              verified bank file.

  F5             24 h / Day 1   24 h           48 h / 24 h    Records Manager
                 08:00                                        accepts secure queue
                                                              and authenticated
                                                              record checks.
  --------------------------------------------------------------------------------

  -----------------------------------------------------------------------
  Checkpoint              At 08:00 Day 0          Potential gap
  ----------------------- ----------------------- -----------------------
  B01 DB01 full, 23:00    9 h old                 Base image alone cannot
  Day −1                                          meet transactional
                                                  RPOs.

  B02 DB01 incremental    1 h old                 Latest recoverable
  through 07:00 Day 0                             point if full
                                                  contiguous chain
                                                  passes.

  B03 AUTH01 snapshot,    8 h old                 Identity changes after
  00:00 Day 0                                     midnight may be absent.

  B04 FS01 full, 23:00    9 h old                 File/permission changes
  Day −1                                          since checkpoint may be
                                                  lost.

  Disconnected full,      63 h old                Fallback, not ordinary
  17:00 Day −3                                    compliant recovery.
  -----------------------------------------------------------------------

The 63-hour age is 7 hours to midnight on Day −3, plus two full 24-hour
days and eight hours on Day 0. In the stipulated successful baseline,
DB01's age is one hour: F1 exceeds its 15-minute target by 45 minutes,
and F2 exceeds 30 minutes by 30 minutes. F3 is at its one-hour boundary;
F4 meets its four-hour transaction-data target. AUTH01 is eight hours
old and exceeds a conservative application-wide RPO for F1--F4; FS01 and
AUTH01 remain inside F5's 24-hour age allowance. Passing checkpoint-age
arithmetic does not establish integrity or successful application
recovery.

To address the gap, propose weekly application-consistent DB01 full
backups, daily differential copies and 15-minute transaction-log or
incremental capture, coordinated with recoverable application versions.
Protect AUTH01 configuration and state after changes and at intervals
designed to support its approved objective; use weekly FS01 full and
daily incremental/version captures. Retain local fast-restore copies,
encrypted geographically separate copies, and an independently
administered immutable or disconnected copy. Proposed operational
retention is seven days locally, 35 days offsite and monthly protected
archives for 12 months, subject to legal retention, capacity, supplier
verification and cost approval (ICDFA, n.d.-b, slide 8).

The precise DB01 restoration chain is B01 full at 23:00 followed by
every required, chronological B02 incremental up to 07:00; individual
increment identifiers are not supplied and must not be fabricated.
Review signed manifests and hashes, encrypted key access, configuration
compatibility, privileged access and post-restore sample transactions.
Production and network-backup administration presently share one
identity; the offsite provider's access independence is undocumented.
Segregate credentials and MFA, test offline access without production
identity, and preserve logs. A live replica can propagate corruption and
is not a substitute for point-in-time protected backups. If any chain
element fails, quarantine it, select the most recent fully verified
alternative, recalculate RPO impact and obtain business-owner approval.
Provider payment references can help reconcile financial entries, but
missing exam answers, unaudited identity changes, and unknown edits
cannot be assumed to be reconstructed (NIST, 2010).

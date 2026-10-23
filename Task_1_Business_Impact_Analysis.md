# Task 1 --- Business Impact Analysis

**Course:** GRC205 --- Business Continuity and Disaster Recovery\
**Assessment scenario:** Northbridge Skills Institute\
**Student:** Ibrahim Abdullahi\
**Registration number:** 2025/GCR/12720

> This file contains the relevant section of the submitted assignment,
> separated for easier review. Supplied scenario details, proposed
> controls, modelled results and caveats are retained as presented in
> the source document.

Business priority follows time-sensitive consequences, learner welfare
and integrity, not only the hourly rate. F1 is first because a failed
11:00 examination incurs immediate educational harm and a one-off cost.
F2 and F3 follow because fee confirmation closes at 16:00 and admissions
at 18:00 on Day 0. F4 payroll bank instructions are due 12:00 on Day 1;
F5 records have a 48-hour internal commitment. Payroll and sensitive
record cases can be escalated despite their lower default ranking
(ICDFA, n.d.-a, pp. 1--4; ICDFA, n.d.-b, slide 5).

  ------------------------------------------------------------------------
  Priority / function;    Affected users,          Minimum acceptable
  owner                   dependency and time      service and control
                          constraint               
  ----------------------- ------------------------ -----------------------
  1\. F1                  120 exam candidates;     Accessible authorized
  Teaching/assessment;    broader learners/tutors. delivery or equitable
  Academic Director       Network, AUTH01, DB01,   rescheduling, candidate
                          LMS01; 11:00 exam; NGN   authentication,
                          60,000/h.                invigilation, signed
                                                   attendance,
                                                   exam-integrity
                                                   approval. Only 25 of 40
                                                   Centre workstations
                                                   supplied.

  2\. F2 Fees/finance;    Payers/finance staff.    Provider-verified
  Finance Manager         Network, AUTH01, DB01,   provisional
                          FIN01 and external       acknowledgement, unique
                          provider; 16:00 fee      transaction IDs, dual
                          confirmation; NGN        review and eventual
                          40,000/h.                reconciliation; do not
                                                   present provisional
                                                   entries as posted
                                                   balances.

  3\. F3 Admissions;      Applicants/registrars.   Time-stamped restricted
  Registrar               Network, AUTH01, DB01,   intake with case
                          REG01; 18:00 close; NGN  references, authorized
                          20,000/h.                cutoff/appeal handling,
                                                   duplicate and
                                                   eligibility
                                                   verification before
                                                   later import.

  4\. F4 Payroll; HR      Up to 90 staff. Network, Last verified payroll
  Manager                 AUTH01, DB01, HR01,      plus approved
                          bank; Day 1 12:00        amendments, independent
                          submission; NGN          HR/Finance sign-off,
                          10,000/h.                bank acknowledgement
                                                   and duplicate
                                                   prevention controls.

  5\. F5                  Learners/alumni/staff.   Restricted request
  Certificates/records;   Network, AUTH01, FS01;   queue; issue authentic
  Records Manager         48-hour commitment; NGN  records only against
                          5,000/h.                 independent verified
                                                   sources and Records
                                                   Manager authority.
  ------------------------------------------------------------------------

People's requirements include service owners, invigilators, learner
accessibility support, independent finance and payroll approvers, the
two designated technicians and trained records staff. Premises must have
safe occupancy, reliable power/connectivity, accessible assessment
arrangements, and restricted record space. Suppliers include
alternative-site operators, the payment provider, bank, connectivity
operators, and offsite backup custodians. Necessary information includes
approved rosters, candidate instructions, transaction references,
payroll mandates, backup catalogues, and protected temporary registers.
Their detailed availability is unverified.

  -----------------------------------------------------------------------
  Function                8-hour worked cost      24-hour worked cost
                          (NGN)                   (NGN)
  ----------------------- ----------------------- -----------------------
  F1                      60,000 × 8 + 120,000 =  60,000 × 24 + 120,000 =
                          600,000                 1,560,000

  F2                      40,000 × 8 = 320,000    40,000 × 24 = 960,000

  F3                      20,000 × 8 = 160,000    20,000 × 24 = 480,000

  F4                      10,000 × 8 = 80,000     10,000 × 24 = 240,000

  F5                      5,000 × 8 = 40,000      5,000 × 24 = 120,000

  TOTAL                   135,000 × 8 + 120,000 = 135,000 × 24 + 120,000
                          1,200,000               = 3,360,000
  -----------------------------------------------------------------------

The five independent rates sum to NGN 135,000 per hour. Both
hypothetical periods include the NGN 120,000 examination-rescheduling
charge exactly once because no acceptable assessment is assumed by
11:00. Rates apply only to the first 24 hours, so extrapolation to 72
hours is invalid. These simplified no-mitigation estimates exclude
uncertain avoided costs and the non-financial consequences of learner
exclusion, reputation, privacy, evidence of integrity and payroll error.
They are not observing losses.

Principal dependencies are concentrated in DB01 (F1--F4), AUTH01 (all
five), and the recovery network. A third major risk is that 40
candidates need center devices, but only 25 workstations exist, leaving
a simultaneous deficit of 15. A fourth is a two-technician competition
for indivisible recovery actions. Consequently, business coordination
must operate temporary services in parallel while technicians obey the
prerequisite sequence; Microsoft 365's email does not replace AUTH01.

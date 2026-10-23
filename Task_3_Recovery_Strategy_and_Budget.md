# Task 3 --- Recovery Strategy and Budget

**Course:** GRC205 --- Business Continuity and Disaster Recovery\
**Assessment scenario:** Northbridge Skills Institute\
**Student:** Ibrahim Abdullahi\
**Registration number:** 2025/GCR/12720

> This file contains the relevant section of the submitted assignment,
> separated for easier review. Supplied scenario details, proposed
> controls, modelled results and caveats are retained as presented in
> the source document.

The annual budget ceiling is NGN 3,000,000. Each package covers five
services and shared infrastructure and requires NGN 400,000 independent
protected backups plus NGN 200,000 training/testing. Recovery windows
are estimates for the first critical service, not validated completion
times for all business functions (ICDFA, n.d.-a, p. 3).

  ------------------------------------------------------------------------------------
  Package        Base +         Total /        Estimated      Capability and
                 backups +      headroom (NGN) first service  limitation
                 tests (NGN)                   / loss         
  -------------- -------------- -------------- -------------- ------------------------
  Cold           600,000 +      1,200,000 /    24--48 h / up  Unacceptable for short
                 400,000 +      1,800,000      to 24 h        F1/F2 objectives; staff
                 200,000                                      must build and restore
                                                              the environment.

  Warm           1,500,000 +    2,100,000 /    3--5 h / 1--6  Feasible provisional
                 400,000 +      900,000        h              foundation; cannot
                 200,000                                      guarantee F1/F2 RTO/RPO;
                                                              rely on approved
                                                              workarounds.

  Hot            2,400,000 +    3,000,000 / 0  About 1 h / up Potentially stronger
                 400,000 +                     to 15 min      objectives; consume
                 200,000                                      entire ceiling and still
                                                              needs tested
                                                              failover/backup/device
                                                              support.
  ------------------------------------------------------------------------------------

Recommend the warm site provisionally: it leaves NGN 900,000 headroom,
avoids cold-site delays, and can support controlled temporary workflows.
Nevertheless, it cannot satisfy F1's two-hour technical restoration
objective in the supplied drill or guarantee 15/30-minute F1/F2 RPOs.
Two technicians, provider access arrangements and independent
geographically/power-diverse premises must be validated. The 15-device
examination shortfall requires supplier-confirmed additional devices, an
integrity-preserving approved alternative, or fair rescheduling. The
Executive Sponsor must expressly accept residual exam, data-loss,
staffing, corruption and supplier risks with Academic/Finance owner
endorsement; if these are unacceptable, reassess hot-site procurement or
revise targets only following an approved BIA review.

The NGN 2,100,000 annual warm-plan cost lies between the hypothetical
eight-hour loss (NGN 1,200,000) and 24-hour loss (NGN 3,360,000). The
difference between the latter and the plan is NGN 1,260,000; this is not
an annual net benefit. One scenario supply neither outage
frequency/probability nor the loss avoided by actual recovery, so annual
ROI cannot be calculated defensibly. Management must obtain outage
history, tested function-specific restoration and data points, supplier
service-level evidence, setup and connectivity quotations,
alternate-site flood exposure, exam equipment cost and security
assurance before spending or accepting promised recovery times.

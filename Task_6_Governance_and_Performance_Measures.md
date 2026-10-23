# Task 6 --- Governance and Performance Measures

**Course:** GRC205 --- Business Continuity and Disaster Recovery\
**Assessment scenario:** Northbridge Skills Institute\
**Student:** Ibrahim Abdullahi\
**Registration number:** 2025/GCR/12720

> This file contains the relevant section of the submitted assignment,
> separated for easier review. Supplied scenario details, proposed
> controls, modelled results and caveats are retained as presented in
> the source document.

The Executive Sponsor approves policy, budget, exceptions and annual
reviews; the BC/DR Coordinator owns controlled plan versions, the
exercise registers and management reporting. Service owners approve
minimum service, the DR Lead validates technical performance, Facilities
owns premises safety, Security reviews protected backup access, and HR
manages responder competence. Store a controlled master,
encrypted/offline emergency role copies, a recipient/access register and
change log. Review at least annually and after flood-risk, premises,
supplier, system, workforce, examination-timetable, privacy or
failed-restore changes. Do not publish live contact lists, credentials
or learner data on a public repository.

The proposed 12-month program includes daily backup monitoring with
weekly exception review; monthly isolated DB01 point-in-time chain
restores; quarterly AUTH01/FS01 restores and 45-minute multi-role
tabletops; semiannual two-tech runbook and service-acceptance
walkthroughs; annual alternate-site/supplier review and management
approval; and onboarding/role-change training. Collect signed
timestamps, recoverable points, access-independence evidence, owner
acceptance and tracked remediation. A simulated schedule does not
satisfy actual test completion.

  -----------------------------------------------------------------------
  Framework                           Coursework alignment
  ----------------------------------- -----------------------------------
  NIST 1 --- Policy                   Task 4 activation/authority, Task 6
                                      ownership and approval

  NIST 2 --- BIA                      Task 1 functions, costs, deadlines
                                      and dependencies

  NIST 3 --- Preventive controls      Task 2 independent protected
                                      backups and flood/power prevention

  NIST 4 --- Strategy                 Task 3 priced alternatives and
                                      residual-risk decision

  NIST 5 --- Contingency plan         Task 4 runbook, temporary workflows
                                      and cutback

  NIST 6 --- Tests/training           Task 5 model/tabletop and Task 6
                                      calendar

  NIST 7 --- Maintenance              Task 6 triggers and controlled
                                      versions

  ISO 22301 context/leadership        Flood, interested parties, sponsor
                                      roles (clauses 4--5)

  ISO planning/support                Objectives, resources,
                                      communication and competence
                                      (clauses 6--7)

  ISO operation                       BIA, continuity procedures,
                                      recovery/exercises (clause 8)

  ISO performance/improvement         Metrics, management review,
                                      corrective actions (clauses 9--10)
  -----------------------------------------------------------------------

The NIST mapping follows SP 800-34 Rev. 1 and the teaching deck slide 4;
ISO alignment is a high-level educational interpretation of ISO 22301
themes on slide 9, not certification. ISO 22301:2019 Amendment 1:2024
requires considering climate issues in context: Northbridge should
assess local floodplain exposure, drainage, rainfall extremes, common
electrical substations and alternate-site hazard correlation before
approving geographic separation (ISO, 2024).

  -----------------------------------------------------------------------
  KPI / measurement       Target; reporting /     Evidence status
                          accountable             
  ----------------------- ----------------------- -----------------------
  Recovery performance =  ≥90% overall; critical  Model only: 4/5 = 80%,
  100 × RTO-compliant     F1 either 100% or       not a live test.
  technical restorations  signed exception. Each  
  / tested functions;     test / DR Lead.         
  report accepted                                 
  business service                                
  separately.                                     

  RPO checkpoint          100% F1/F2 critical;    Model age comparison:
  compliance = 100 ×      ≥95%. Monthly/quarterly 4/10 = 40%; not
  compliant verified      / DR + Security.        successful restore
  function-dependency                             evidence.
  points / assessed                               
  points.                                         

  Restore-test coverage = 100% annually;          Not measured in real
  100 × critical assets   quarterly / BC          operations.
  restore-tested /        Coordinator.            
  critical assets                                 
  inventoried.                                    

  On-time action closure  ≥90%; zero P1 overdue   Eight simulated
  = 100 × due actions     without exception.      proposed actions; no
  evidenced closed on     Monthly / BC            real closure reported.
  time / all actions due. Coordinator.            

  Training completion =   ≥95%; 100% command      Not measured; real
  100 × trained assessed  decisionmakers.         roster absent.
  responders / assigned   Quarterly / HR.         
  responders.                                     

  Plan currency = 100 ×   100%. Quarterly / BC    Not measured; plan is
  in-date and             Coordinator.            an academic proposal.
  trigger-reviewed plans                          
  / approved plans.                               
  -----------------------------------------------------------------------

Using the teaching slide 13 model (Initial, Developing, Defined,
Managed, Optimizing), the fictional case supports an indicative Level 2
(Developing) planning position rather than a verified maturity score:
some backups and modelled runbook activity exist, but independent
access, tested restores and sufficient examination devices remain
unproven. A credible 12-month goal is Level 3 (Defined): Months 1--3
approve roles, objectives and supplier risks; Months 4--6 segregate
backup access and verify DB01/AUTH01/FS01 restores; Months 7--9 perform
documented drills and training; Months 10--12 demonstrate recurring
measurement, closure evidence and signed management review. If exam
delivery or protected restores remain unsupported, retain Level 2 rather
than declare achievement.

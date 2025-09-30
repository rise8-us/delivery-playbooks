# Problem Statement Framing

## 1) Identify and contextualize the problem

The first step in writing a problem statement is to spot the issue, and start gathering data. Step into the environment where the problem happens—whether in support, production, or somewhere else—and try to experience it firsthand. Begin to connect how this problem currently effects the mission or business.

After seeing the problem for yourself, talk to the people closest to it. That might include support teams, cross-functional partners, or anyone with hands-on documentation. Additionally, leverage user and stakeholder research to also map out the full scope of the problem.

1. What is the problem?
2. What symptoms do we notice about the problem space?
3. How have we tried to solve this problem before? Why didn't that work?
4. What assumptions and biases surround this problem?
5. What do we know to be true about this problem? What data do we have on hand?
6. Who experiences the problem?
7. When, where and how do they experience it?
8. What consequences are produced by the problem?
9. How do individual lived experiences alter those current outcomes?
10. How does this measurably impact the mission/business today?

## 2) Find the root cause

This is the opportunity to really dig into the "why" questions behind the issue to identify its origin point. To do this we often consider changing the way we look at the problem, so that we can get closer to the root cause and challenge our initial framing.

### The 5 whys method

This technique involves asking a series of “why”s until you eventually uncover the root cause—the real “why” beneath all those other “why”s. It's a lightweight root-cause analysis method where a team repeatedly asks “Why?” (usually ~5 times) about a clearly stated problem until it reaches a systemic, actionable cause that—if fixed—would have prevented the problem from occurring.

#### Why it's valuable

* **Fast & low-overhead**: No fancy tools required; 30–60 minutes with the right people can reveal the real blocker.
* **Builds shared understanding**: Cuts through opinions to converge on evidence-backed cause(s).
* **Targets leverage points**: Ends at process, policy, environment, or design gap you can change.

#### Limits to be aware of

5 Whys can oversimplify complex/entangled causes if used dogmatically. Treat it as a why-tree (branch when needed), require evidence for each why, and stop when you hit a controllable, testable cause.

#### When to use it

Use 5 Whys when:

* The problem is specific, observable and/or measurable.
* You have access to the people and data closest to the work.
* You need speed and a first, credible root cause to drive corrective and preventive actions (CAPA).

Avoid or augment when:

* The issue is multi-factor across teams/systems (use a fishbone diagram first to fan out categories, then 5 Whys on the top suspects).
* You lack trust/psychological safety (address that first or use an async, blameless write-up).
* The “problem” is strategic/market-level (use Impact Mapping, hypothesis tests, or discovery methods instead).

#### How to prepare a 5 whys session

* **Crisp problem statement**: what happened, where, when, scope, and impact/metric (e.g., “Checkout error rate spiked from 0.2% to 3.4% on 2025-09-28 between 12:00–14:00 CT; revenue down 7% hour-over-hour.”)
* **Evidence at hand**: logs, screenshots, event timeline, change list, user reports—enough to verify each “why.”
* **The right people**: 5–8 cross-functional participants who touch detection, diagnosis, fix, and prevention (facilitator + scribe included).
* **Working agreements**: blameless approach, one conversation at a time, challenge ideas with data, not people.
* **Timebox**: 45–60 minutes for the workshop; 15 minutes after for actions.

#### How to run it

##### Prep (10–15 min before)

1.Grab a copy of [5 Whys template](https://www.figma.com/board/noltgJqNPddIymd4r8AjJm/5-Whys-Analysis?node-id=0-1&p=f&t=igdr8EM7yhU4IJrh-0)

2. Assign roles

    * Facilitator: keeps it blameless, probes for evidence, manages time.
    * Scribe: captures the chain(s), decisions, owners, due dates.

3. Set the frame

    * Write the problem statement and impact metric big and visible.
    * Draw a simple why-tree: problem at the top; each “why” as a node; allow branches when multiple plausible causes appear.

3. Collect quick facts

    * Timeline of events, recent changes, alerts, relevant tickets.

##### Facilitate the 5 Whys (30–40 min)

1. **Why #1 — Proximate cause**

    * Ask: “Why does this happen?” "What causes this to happen?" 
    * Require evidence: “What observation/log shows that?”

2. **Why #2–#4 — Mechanism & enabling conditions**

    * For each answer, ask follow up “Why?” based questions
    * If multiple plausible answers emerge, branch and pursue the most impactful/likely first.
    * Continually test: Would fixing this have prevented the problem?

3. **Why #5 (±2) — Systemic cause**

    * Stop when you reach a controllable, systemic cause (policy, process, tooling, environment, design, staffing, training, incentives).
    * If you land on “human error,” go one more why to reveal the system, process, political or other gap that allowed it.

4. **Validate**

    * Cross-check with data or a quick experiment (“If X were true, would event Y still occur?”).
    * If uncertainty remains, mark a learning action (small test) rather than guessing.

5. **Converge on the primary root cause(s)**

    * You may end with 1–3 root causes across branches.
    * Link to VSM, User Experience Maps or DDD artifacts: Map where the cause lives in the value stream, user journey or system behavior designs.

##### Capture potential actions for causes

One simple way to turn root-causes into potential next steps for the team, is to ideate on Corrective and Preventative Actions (CAPA)

* **Containment**: immediate guardrails to reduce risk of this problem recurring (feature flag, hotfix, alert).
* **Corrective**: introduce a change to stop recurrence in the short term (procedure, check, test).
* **Preventive**: design/process improvement that makes the failure mode impossible or highly unlikely (automation, architecture, training, policy, incentives).


##### Facilitator cheat-sheet phrases

* “What evidence supports that why?”
* “If we fixed this, would the problem still occur?”
* “What system made that outcome likely?”
* “Let’s branch: note both hypotheses, and start with the one with the biggest impact.”
* “We’re not judging people—we’re improving the system.”

##### Examples

| Domain                            | Problem (metric & impact)                                                                         | 5 Whys (evidence-led chain)                                                                                                                                                                                                                                                                                                                                                                                                                                 | Root Cause (systemic)                                                                                                                                             | CAPA Examples — Containment / Corrective / Preventive                                                                                                                                                                                                                                                                                               | Validation Metrics                                                                                                              |
| --------------------------------- | ------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| **Developer Platform**            | **Service onboarding takes 15 days** (target ≤5); teams miss milestones and spin up shadow infra. | 1) Onboarding tickets sit **idle ~6 days**. *(Jira cycle-time report)*  2) Approvals are **manual and batched weekly**. *(SOP, approver calendar)*  3) Approvers **fear over-provisioning** without standardized roles. *(interviews)*  4) **No codified IAM policy packs**; each request needs bespoke review. *(repo audit)*  5) Platform backlog **prioritized features over governance**; no OKR for time-to-first-commit. *(backlog history, OKR doc)* | Missing **least-privilege IAM policy packs** and **self-service provisioning** policy, driven by misaligned prioritization.                                       | **Containment:** Daily approval SLA; temporary pre-approved “starter” roles.  **Corrective:** Ship 3 standardized IAM policy packs (read-only, contributor, admin) with guardrails; add request form validation.  **Preventive:** Terraform module + policy-as-code tests in CI; platform OKR on **TTFC**; monthly access review.                   | Median **Time-to-First-Commit ≤5 days**; **≥80%** of onboardings fully self-service; zero shadow infra exceptions in a quarter. |
| **Dept of Veterans Affairs (VA)** | **Claims status data >72 hours stale**; call center volume **+35%**; Veteran trust at risk.       | 1) Nightly ETL **failed two nights**. *(Airflow logs)*  2) Source API was **rate-limited (429s)**. *(HTTP logs)*  3) Batch window **overlapped partner’s peak** after their schedule change. *(partner notice)*  4) **No alerting/backoff** for 429s; rigid schedule. *(observability config)*  5) **No SLO/clear ownership** for data freshness across data eng/integration teams. *(RACI, SLO gap)*                                                       | Absent **ownership & SLO for data freshness**, leaving **rate-limit failures unmonitored** and schedules inflexible.                                              | **Containment:** Manual re-run off-peak; throttle requests.  **Corrective:** 429 alerting; exponential backoff + retry; reschedule to partner off-peak.  **Preventive:** Define **Data Freshness SLO (P95 < 6h)**; RACI ownership; partner-schedule change webhook; migrate critical flows to **event-driven** ingestion.                           | Sustain **P95 freshness < 6h** for 30 days; call volume returns to baseline; 0 unacknowledged 429 episodes per month.           |
| **Dept of State**                 | **Passport median processing = 14 weeks** (target ≤8); public service delays and backlog growth.  | 1) **Manual review queue +60%**. *(queue metrics)*  2) Photo auto-screen **flag rate 40%** (↑). *(model logs)*  3) New vendor **model sensitivity increased**. *(release notes)*  4) Deployed **without calibration/shadow testing**. *(QA plan)*  5) **No representative, privacy-approved dataset** or governance to validate model; **no DSA** enabling safe testing. *(legal/policy audit)*                                                             | **Model governance gap:** photo-screening model deployed without **calibrated, representative validation** due to missing data-governance & shadow-test protocol. | **Containment:** Lower sensitivity / rollback; add human-in-the-loop triage shifts.  **Corrective:** Create privacy-approved **synthetic dataset**; run **shadow test** vs prior model; calibrate threshold.  **Preventive:** Formal **ML governance** (pre-prod shadowing, bias/error checks, sign-off); vendor **DSA**; ongoing drift monitoring. | Median processing **≤8 weeks**; manual-review rate **≤15%**; false-positive photo flags **≤5%** sustained.                      |

<br/>

## 3) Refine problem statements

The following templates will ensure problem statements are specifc, actor-focused, and aligned to results that matter.

### Option one

* **I am a** *[persona of interest; could be users, stakeholders, services or even entire systems].*
* **I'm trying to** *[accomplish a task, job-to-be-done, goal],*
* **but** *[the problem or challenge they're experiencing]*
* **because** *[the root cause to our problem/challenge]*
* **which makes me feel** *[emotion/sentiment]*
* **and contributes to** *[current mission/business impact condition].*

#### Exmaples

| Domain                   | Scenario                                         | Problem Statement (preferred format)                                                                                                                                                                                                                                                                                                                                                                                                                  |
| ------------------------ | ------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Developer Platforms      | OAuth onboarding & docs                          | I am a partner developer integrating OAuth 2.0. I’m trying to complete authentication and make my first successful API call, but I keep receiving token errors and 4xx responses on day one because the quickstart examples are inconsistent across languages and the doc flow buries required parameters. Which makes me feel frustrated and uncertain, and contributes to delayed integrations, higher support ticket volume, and early churn risk. |
| Developer Platforms      | FedRAMP/ATO-friendly CI                          | I am a federal platform engineer. I’m trying to pass security scans in CI to move toward ATO, but my builds fail on approved runners because there are no STIG-hardened base images or signed SBOMs available. Which makes me feel blocked and anxious about compliance timelines, and contributes to missed delivery milestones and stalled accreditation.                                                                                           |
| Developer Platforms      | Webhooks reliability in sandbox                  | I am a backend engineer. I’m trying to validate webhooks end-to-end before production, but I can’t reliably replay events because the platform sandbox lacks message retry and an easy tunnel for local testing. Which makes me feel nervous about hidden failure modes, and contributes to production rollbacks and longer incident MTTR.                                                                                                            |
| Developer Platforms      | Quotas & rate limits                             | I am an API consumer on a new team. I’m trying to achieve time-to-first-2xx under 30 minutes, but I keep hitting rate limits unexpectedly because default quotas and 429 guidance are undocumented in the quickstart. Which makes me feel confused and stuck, and contributes to false incident escalations and wasted engineering time.                                                                                                              |
| Developer Platforms      | Cross-SDK observability                          | I am an SRE on call. I’m trying to triage an incident quickly, but traces and metrics are inconsistent across official SDKs because they ship different OpenTelemetry versions and naming conventions. Which makes me feel blind during outages, and contributes to longer MTTR and SLO breaches.                                                                                                                                                     |
| Dept of Veterans Affairs | Post-discharge enrollment                        | I am a recently discharged Veteran. I’m trying to enroll in primary care and benefits, but I have to re-enter the same information across multiple portals because systems aren’t integrated for identity and data reuse. Which makes me feel exhausted and discouraged, and contributes to delayed access to care and increased no-shows.                                                                                                            |
| Dept of Veterans Affairs | Caregiver respite scheduling                     | I am a family caregiver. I’m trying to schedule respite care, but appointment availability is a black box because clinic calendars and eligibility checks aren’t synchronized. Which makes me feel helpless and burned out, and contributes to missed appointments and avoidable emergency visits.                                                                                                                                                    |
| Dept of Veterans Affairs | Claims intake system (system persona)            | I am the claims intake system. I’m trying to accept complete submissions the first time, but I receive duplicate and abandoned forms because session timeouts are aggressive and progress saving is unclear. Which makes me feel overloaded and inefficient, and contributes to a growing backlog and longer decision timelines.                                                                                                                      |
| Dept of Veterans Affairs | Medical records acquisition                      | I am a VA claims processor. I’m trying to verify medical evidence quickly, but provider records arrive late or via fax because there’s no reliable electronic exchange with key networks. Which makes me feel overwhelmed, and contributes to 30+ day stalls and dissatisfaction for Veterans.                                                                                                                                                        |
| Dept of Veterans Affairs | Rural telehealth access                          | I am a rural Veteran. I’m trying to attend a video visit, but my connection drops repeatedly because the app is bandwidth-heavy and my area lacks broadband. Which makes me feel embarrassed and neglected, and contributes to missed visits and worsening health outcomes.                                                                                                                                                                           |
| Dept of State            | Visa category selection                          | I am a first-time traveler. I’m trying to select the correct visa category, but I often choose the wrong form because eligibility rules are buried in lengthy policy PDFs. Which makes me feel confused and anxious, and contributes to abandoned applications and rework at consulates.                                                                                                                                                              |
| Dept of State            | Emergency passport appointments abroad           | I am a U.S. citizen abroad. I’m trying to book an emergency passport appointment, but no slots appear for days because there’s no waitlist or auto-reassignment when cancellations occur. Which makes me feel stranded and stressed, and contributes to travel disruptions and hotline overload.                                                                                                                                                      |
| Dept of State            | Cross-system applicant identity                  | I am a consular officer. I’m trying to adjudicate cases efficiently, but I keep encountering duplicate or mismatched records because there is no single applicant identifier across legacy systems. Which makes me feel frustrated and error-prone, and contributes to longer processing times and increased denial appeals.                                                                                                                          |
| Dept of State            | Student (F-1) processing                         | I am an international student applicant. I’m trying to complete my F-1 application on time, but my I-20 uploads fail intermittently because the SEVIS integration times out under peak load. Which makes me feel worried about missing my start date, and contributes to rescheduling and school intake delays.                                                                                                                                       |
| Dept of State            | Appointment scheduling platform (system persona) | I am the visa appointment scheduling platform. I’m trying to help applicants confirm slots reliably, but many drop off at confirmation because time zones and local holidays aren’t surfaced clearly. Which makes me feel inefficient and brittle, and contributes to high no-show rates and uneven consular utilization.                                                                                                                             |

<br/>

### Option two




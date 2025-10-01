# The 5 whys method

This technique involves asking a series of “why”s until you eventually uncover the root cause—the real “why” beneath all those other “why”s. It's a lightweight root-cause analysis method where a team repeatedly asks “Why?” (usually ~5 times) about a clearly stated problem until it reaches a systemic, actionable cause that—if fixed—would have prevented the problem from occurring.

## Why it's valuable

* **Fast & low-overhead**: No fancy tools required; 30–60 minutes with the right people can reveal the real blocker.
* **Builds shared understanding**: Cuts through opinions to converge on evidence-backed cause(s).
* **Targets leverage points**: Ends at process, policy, environment, or design gap you can change.

## Limits to be aware of

5 Whys can oversimplify complex/entangled causes if used dogmatically. To avoid this outcome, teams should consider the following principles:

* Treat it as a why-tree (branch when needed)
* Require evidence for each why
* Stop when you hit a controllable, and testable cause

## When to use it

Use 5 Whys when:

* The problem is specific, observable and/or measurable.
* You have access to the people and data closest to the work.
* You need speed and a first, credible root cause to drive corrective and preventive actions (CAPA).

Avoid or augment when:

* The issue is multi-factor across teams/systems (use a fishbone diagram first to fan out categories, then 5 Whys on the top suspects).
* You lack trust/psychological safety (address that first or use an async, blameless write-up).
* The “problem” is strategic/market-level (use Impact Mapping, hypothesis tests, or discovery methods instead).

## How to prepare a 5 whys session

* **Crisp problem statement**: what happened, where, when, scope, and impact/metric (e.g., “Checkout error rate spiked from 0.2% to 3.4% on 2025-09-28 between 12:00–14:00 CT; revenue down 7% hour-over-hour.”)
* **Evidence at hand**: logs, screenshots, event timeline, change list, user reports—enough to verify each “why.”
* **The right people**: 5–8 cross-functional participants who touch detection, diagnosis, fix, and prevention (facilitator + scribe included).
* **Working agreements**: blameless approach, one conversation at a time, challenge ideas with data, not people.
* **Timebox**: 45–60 minutes for the workshop; 15 minutes after for actions.

## How to run it

### Prep (10–15 min before)

1. Grab a copy of [5 Whys template](https://www.figma.com/board/noltgJqNPddIymd4r8AjJm/5-Whys-Analysis?node-id=0-1&p=f&t=igdr8EM7yhU4IJrh-0), or search and add the template directly into your existing Figjam board

2. Assign roles

    * Facilitator: keeps it blameless, probes for evidence, manages time.
    * Scribe: captures the chain(s), decisions, owners, due dates.

3. Set the frame

    * Write the problem statement and impact metric big and visible.
    * Draw a simple why-tree: problem at the top; each “why” as a node; allow branches when multiple plausible causes appear.

3. Collect quick facts

    * Timeline of events, recent changes, alerts, relevant tickets.

### Facilitate the 5 Whys (40 min)

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
    * Link to VSM, User Experience Maps, DDD Event Storm maps, or other artifacts.
  
### Capture potential actions for causes

One simple way to turn root-causes into potential next steps for the team, is to ideate on Corrective and Preventative Actions (CAPA)

* **Containment**: immediate guardrails to reduce risk of this problem recurring (feature flag, hotfix, alert).
* **Corrective**: introduce a change to stop recurrence in the short term (procedure, check, test).
* **Preventive**: design/process improvement that makes the failure mode impossible or highly unlikely (automation, architecture, training, policy, incentives).

### Facilitator cheat-sheet phrases

* “What evidence supports that why?”
* “If we fixed this, would the problem still occur?”
* “What system made that outcome likely?”
* “Let’s branch: note both hypotheses, and start with the one with the biggest impact.”
* “We’re not judging people—we’re improving the system.”

## Examples

| Domain                            | Problem (metric & impact)                                                                         | 5 Whys (evidence-led chain)                                                                                                                                                                                                                                                                                                                                                                                                                                 | Root Cause (systemic)                                                                                                                                             | CAPA Examples — Containment / Corrective / Preventive                                                                                                                                                                                                                                                                                               | Validation Metrics                                                                                                              |
| --------------------------------- | ------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| **Developer Platform**            | **Service onboarding takes 15 days** (target ≤5); teams miss milestones and spin up shadow infra. | 1) Onboarding tickets sit **idle ~6 days**. *(Jira cycle-time report)*  2) Approvals are **manual and batched weekly**. *(SOP, approver calendar)*  3) Approvers **fear over-provisioning** without standardized roles. *(interviews)*  4) **No codified IAM policy packs**; each request needs bespoke review. *(repo audit)*  5) Platform backlog **prioritized features over governance**; no OKR for time-to-first-commit. *(backlog history, OKR doc)* | Missing **least-privilege IAM policy packs** and **self-service provisioning** policy, driven by misaligned prioritization.                                       | **Containment:** Daily approval SLA; temporary pre-approved “starter” roles.  **Corrective:** Ship 3 standardized IAM policy packs (read-only, contributor, admin) with guardrails; add request form validation.  **Preventive:** Terraform module + policy-as-code tests in CI; platform OKR on **TTFC**; monthly access review.                   | Median **Time-to-First-Commit ≤5 days**; **≥80%** of onboardings fully self-service; zero shadow infra exceptions in a quarter. |
| **Dept of Veterans Affairs (VA)** | **Claims status data >72 hours stale**; call center volume **+35%**; Veteran trust at risk.       | 1) Nightly ETL **failed two nights**. *(Airflow logs)*  2) Source API was **rate-limited (429s)**. *(HTTP logs)*  3) Batch window **overlapped partner’s peak** after their schedule change. *(partner notice)*  4) **No alerting/backoff** for 429s; rigid schedule. *(observability config)*  5) **No SLO/clear ownership** for data freshness across data eng/integration teams. *(RACI, SLO gap)*                                                       | Absent **ownership & SLO for data freshness**, leaving **rate-limit failures unmonitored** and schedules inflexible.                                              | **Containment:** Manual re-run off-peak; throttle requests.  **Corrective:** 429 alerting; exponential backoff + retry; reschedule to partner off-peak.  **Preventive:** Define **Data Freshness SLO (P95 < 6h)**; RACI ownership; partner-schedule change webhook; migrate critical flows to **event-driven** ingestion.                           | Sustain **P95 freshness < 6h** for 30 days; call volume returns to baseline; 0 unacknowledged 429 episodes per month.           |
| **Dept of State**                 | **Passport median processing = 14 weeks** (target ≤8); public service delays and backlog growth.  | 1) **Manual review queue +60%**. *(queue metrics)*  2) Photo auto-screen **flag rate 40%** (↑). *(model logs)*  3) New vendor **model sensitivity increased**. *(release notes)*  4) Deployed **without calibration/shadow testing**. *(QA plan)*  5) **No representative, privacy-approved dataset** or governance to validate model; **no DSA** enabling safe testing. *(legal/policy audit)*                                                             | **Model governance gap:** photo-screening model deployed without **calibrated, representative validation** due to missing data-governance & shadow-test protocol. | **Containment:** Lower sensitivity / rollback; add human-in-the-loop triage shifts.  **Corrective:** Create privacy-approved **synthetic dataset**; run **shadow test** vs prior model; calibrate threshold.  **Preventive:** Formal **ML governance** (pre-prod shadowing, bias/error checks, sign-off); vendor **DSA**; ongoing drift monitoring. | Median processing **≤8 weeks**; manual-review rate **≤15%**; false-positive photo flags **≤5%** sustained.                      |

<br/>

## Next steps

Once we've captured the root causes to problems we want to solve, we need to refine and prioritize them.

1. Leverage our [**Problem Statement Framing**](https://delivery-playbooks.rise8.us/content/plays/product/problem-statement-framing/) play to ensure the issue is clear, concise, actor-centric and aligned to measurable results.

2. Leverage a 2x2 matrix or another favorite prioritization technique (e.g. dot voting), and select the root causes that we believe need to be addressed next.
    
    * You need to determine the axes, and scope the definitions for each, that best aligns with your situational decision-making.
    * Basic axis example for validated causes we want to prioritize could look like x = Value ("more or less value if we solve") and y = Effort ("requires more or less effort to solve").

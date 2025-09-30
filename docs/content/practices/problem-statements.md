# Problem Statements

> Practical approaches that lead to more predictable changes in user/system behavior and greater mission impact

## What are problem statements?

A problem statement is a clear, concise, and focused description of an issue that could be solved, serving as a critical alignment tool for delivery teams and a guide for solution exploration. Mastering problem statements prevents misunderstandings, ensures everyone is working towards the same goal, and focuses delivery efforts on the right challenge for users, systems and the mission, leading to greater chances for overall success. An effective problem statement is clear, specific, identifies the affected actors, details the impact, and establishes the desired result.

### Why getting problem statements is important

* **Alignment & Focus**: It ensures the entire team understands and prioritizes a specific problem to solve.
* **Prevents Wasted Effort**: Unclear problem statements lead teams into building solutions for the wrong issue, - wasting time and resources.
* **Guides Solution Exploration**: A well-crafted problem statement acts as a roadmap, keeping delivery efforts targeted and relevant to the actual problem.
* **Measurable Success**: Sets objective-based success criteria, allowing delivery teams to verify we've effectively addressed the original problem.

### What makes an effective problem statement?

An effective problem statement includes the following key components, and will help drive prioritization conversations: 

* **The Current Situation**: A clear, unambiguous description of the current conditions where the issue or unmet need occurs.
* **The Context**: Background information to give the problem meaning and explain why it's an issue now.
* **Who/What it Affects**: Identifying the specific actors (e.g. users, stakeholders or systems) impacted by the problem.
* **Measurability**: Empowers delivery teams to set benchmarks and track progress towards a target, guiding the effectiveness of proposed solutions.
* **Clarity & Conciseness**: It should be simple enough for anyone to understand on the first read, avoiding jargon and fluff.
* **Specificity**: Providing concrete details about the problem's scope rather than being vague or broad.
* **Objectivity**: Presenting the facts about the problem without introducing bias, and avoiding any mention of a presupposed solution.

### Outcome in prod causal chain sweet spot

When we generate and refine problem statements that set the scene for delivering outcomes in prod, it's beneficial to imagine them as a causal chain. By doing so, we not only align everyone to what we're solving, why it is important, and how we will measure success, but it also simplifies how we structure the results of our hypothesis experiments. Specifically, when we adopt a causal chain mindset with our experiment narratives, the after-effect will be similar to our problem statement framing - thus making before and after statements more clear and concise.

**Causal Chain Framing Example**:
> Because of [context], our actor experiences [current condition pain-point or challenge context] which causes [current mission impact conditions]. 

#### Outcome in prod hypothesis experiment example

**Problem**: *Veterans often leave appointments relying on memory to manage complex medication regimens (context). This leads to confusion, missed doses, and adverse interactions (current condition challenges)—driving down adherence to 70% and increasing readmission rates to 25.7% (current mission impact conditions).*
**Hypothesis**: *We believe that auto-generating personalized digital medication summaries (indicating what each drug is for, when to take it, and for how long) will result in greater Veteran understanding and adherence, while reducing admission rates.*
**Outcome target**: *Our hypothesis is valid if ≥60% of Veterans view the summary within 48 hours, and ≥80% report that their medication plan is clear and easy to follow (target behavior change conditions).*
**Impact target**: *Leading to an +8% improvement in monthly medication adherence (70% → 78%), and 2.5% drop in monthly readmission rate (25.7% → 23.2%) (target mission impact conditions).*

### Good vs. bad problem statement examples

Below are examples of problem statements that either intentionally leverage key components (i.e. "good problem statement"), and examples where we illustrate common pitfalls (i.e. "bad problem statements").

| Domain                         | Scenario                                        | **Bad** problem statement                                                            | Why it’s bad                                                                                           | **Good** problem statement                                                                                                                                                                                                                                                                                                                                                                                                                                                             | Why it’s good                                                                                                               |
| ------------------------------ | ----------------------------------------------- | ------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------- |
| Developer Platforms            | API Authentication Onboarding                   | “Our OAuth flow is terrible and confusing; we need a new auth system ASAP.”          | Vague (“terrible”), solution-biased (“need a new auth system”), no context, no actors, not measurable. | *In the last 90 days* (**time**), *41% of first-time partner developers* (**who**) *failed to obtain a valid OAuth2 token within 30 minutes in the sandbox* (**current situation**), *leading to a 23% onboarding abandonment rate and ~180 support tickets/month* (**impact**). *This pattern began after the June 1 v3 documentation migration and affects ~220 partner teams/quarter* (**context/scope**).                                                                          | Timeframe and location stated; actors named; rates/volumes given; triggering event cited; **no implied solution**.          |
| Developer Platforms            | SDK Build Failures (Apple Silicon)              | “X SDK is broken on Macs; we should rewrite the build pipeline.”                     | Overgeneralized (“broken”), prescribes a solution, lacks data and scope.                               | *Since the 4.2.0 release on Aug 5* (**context/time**), *18% of arm64 (Apple Silicon) SDK builds* (**specific**) *fail during linking on macOS 14 in the default template* (**current state**), *affecting ~480 external developers/month and increasing time-to-integration by a median of 2.1 days* (**impact**). *Failures occur across three repos that share the same linker flags* (**specificity/objectivity**).                                                                 | Precise conditions, platform/versions, affected population, measurable impact, **no solution baked in**.                    |
| Dept. of Veterans Affairs (VA) | Disability Claims Delays (Medical Records)      | “Providers are slow; we need an automated medical record importer right now.”        | Assigns blame, prescribes a solution, no data/timeframe/actors.                                        | *Across Q3* (**timeframe**), *32% of disability claims exceeding 90 days* (**specific cohort**) *are delayed due to incomplete external medical records at intake* (**current situation**). *62% of these cases involve requests sent by fax to community providers* (**context**), *affecting ~18,000 Veterans and increasing median processing time by 21 days* (**who/impact**).                                                                                                    | Evidence-based, identifies where delay occurs, quantifies impact, objective and non-prescriptive.                           |
| Dept. of Veterans Affairs (VA) | Missed Appointments (Caregiver-Linked Veterans) | “Our reminders are bad; let’s switch everything to SMS.”                             | Solution-first, vague (“bad”), no baseline, no segment.                                                | *From May–Aug* (**time window**), *no-show rates for primary care among Veterans with a designated caregiver* (**who**) *increased from 8% to 13%* (**measurable change**). *Audit logs show 71% of reminders were sent during weekday work hours only and 46% did not include the caregiver on file* (**context/specificity**), *affecting ~12,400 appointments across 22 facilities* (**scope**).                                                                                    | Clear segment; baseline vs. current; operational context; scope; **no implied solution**.                                   |
| Dept. of State (DoS)           | Wrong Visa Form Starts                          | “People keep picking the wrong visa; we should add a fancy AI triage widget.”        | Solution-biased, vague (“people”), lacks magnitude/context.                                            | *During peak travel months (May–Aug 2025)* (**context/time**), *15% of nonimmigrant visa applicants initiating online applications* (**who**) *start with the wrong visa class and 28% of those abandon before submission* (**measurability**). *Misclassification is concentrated on mobile devices and on pages summarizing eligibility rules from PDF policy memos* (**specific context**), *affecting ~140,000 applicants and increasing call-center volume by ~11%* (**impact**). | Quantifies problem and impact; names where it happens; identifies affected population; objective; **no solution language**. |
| Dept. of State (DoS)           | Overseas Passport Renewal Appointments          | “The consulate scheduling site is awful; we need to rebuild it with a modern stack.” | Subjective (“awful”), solution-first, no evidence/scope.                                               | *Across 11 consulates in EMEA between Jun–Sep 2025* (**time/context**), *19% of passport renewal appointments booked online resulted in no-shows* (**measure**). *Event data indicate 63% of no-shows involved time-zone mismatches between the booking UI and local appointment calendars* (**specific root condition**), *impacting ~9,800 applicants and creating daily idle capacity equivalent to 2.3 staff hours per post* (**impact/scope**).                                   | Concrete timeframe; population; root condition; quantifiable impact; **no prescribed solution**.                            |

<br/>

### Quality litmus test

Use this litmus test on any problem statement draft, and if any box is unchecked, refine before moving on to solution exploration

| Question                            | What to check                                                                                    |
| ----------------------------------- | ------------------------------------------------------------------------------------------------ |
| Current Situation & Context clear?  | Where/when it happens; triggering events; environment (e.g., sandbox, consulate, fax workflows). |
| Who/What it affects named?          | Specific users, segments, facilities, systems, or repositories.                                  |
| Measurable baseline/impact present? | Rates, counts, time, cost, capacity deltas; comparable before/after or trend windows.            |
| Clear, concise, specific?           | Avoid adjectives/blame; include versions, locations, timeframes.                                 |
| Objective and solution-free?        | States facts without prescribing or hinting at a specific fix.                                   |

<br/>

### How to generate problem statements

Check out our [problem statement framing play](https://delivery-playbooks.rise8.us/content/plays/product/problem-statement-framing/).

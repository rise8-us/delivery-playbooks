# Data and Metrics Collection

## What is it?

Data & Metrics Collection is the disciplined way we capture, govern, and interpret evidence to learn whether our products, services or processes are achieving the desired outcomes, and improving the mission. At Rise8, we don’t collect metrics for metrics’ sake. We focus on what the *Lean Analytics* community calls the “One Metric That Matters” (more commonly referred to as ***One Mission Metric that Matters*** in our Rise8 context), and the smallest useful set of inputs that move it.

Aligning everyone on context that is relevant to the problem space we're solving, will ensure that we balance the application of both quantitative and qualitative data, metrics and ultimately insights. The combination helps delivery teams build better hypotheses, smarter experiments, and stronger empirical evidence for what's working — or not.

## Why is it important?

As highlighted in books like *Lean Startup*, *The Four Disciplines of Execution*, and thought leader posts across the product world on OMTM, Objectives and Key Results (OKRs) and Key Performance Indicators (KPIs), effective teams use data as a compass. Here’s why that matters for us:

1. **Diagnose & optimize:** Reveal where we’re winning, stalling, or wasting effort.
2. **Decide with evidence:** Replace anecdotes with signal; make pivot/persevere calls confidently.
3. **Align to mission:** Tie product work to agency outcomes and program value.
4. **Build trust:** A shared, versioned source of truth creates transparency across teams.
5. **Prevent metric drift:** Governance keeps definitions stable, auditable, and hard to game.

If we can’t measure it, we can’t manage it. But just as important — if we measure the wrong thing, we may manage in the wrong direction.

### Principles

1. **Outcomes before outputs:** Instrument for user/system behavior that leads to mission results.
2. **Questions before dashboards:** Start from decisions you need to make; collect just enough to decide.
3. **Quality over quantity:** Favor % Complete & Accurate, freshness, and coverage over vanity counts.
4. **Leading indicators first:** Guide course-corrections early; confirm with lagging indicators later.
5. **Version everything:** Treat metric definitions as code; own them, review them, change-log them.
6. **Ethical by design:** Minimize data collected; protect data types like PII/PHI; document risks and consent.

### What makes a good metric

1. ***Actionable:*** A good metric changes how we behave, or what decisions to make. In other words, it tells us what we should do differently based on the change we see (or not). A vanity metric would be the opposite, and they are typically a data point that looks impressive on the surface but doesn't provide useful, actionable insights into an organizations actual performance or progress towards its goals. (e.g. social media likes or follows, website page views, app downloads, or total registered users)

> Ratios, rates, comparisons over time, across segments, and against competitors  

2. ***Accessible:*** A good metric is easy to understand and remember. If people don't understand the metric, they won't remember it or think about it which means they won't take action on it. We should be able to easily get the data, and the feedback loop between taking action and seeing results should be short.

3. ***Auditable:*** The metric has to be credible to the people who drive the vision and mission; everyone including sponsors and skeptics should be able to audit it.

## What are leading & lagging indicators

Leading indicators are forward-looking, providing predictive insights into future performance by measuring activities or conditions that influence eventual outcomes, while lagging indicators are backward-looking, measuring past results or events that have already occurred. Leaders use lagging indicators to assess past success and leading indicators to guide proactive measures and ensure future goals are met.

- **Leading indicators** move first. They are inputs you can influence now that predict an outcome.
- **Lagging indicators** move after the outcome happens. They confirm impact and are harder to change quickly.

> Rule of thumb: If you can move it this week/sprint and it should move the mission metric later, it’s leading. If it proves the mission moved (often after a delay), it’s lagging.

### Outcome in Prod Mental Model

Inputs (leading)  →  Behavior Outcomes (mix leading & lagging)  →  Mission Impact (lagging)

Examples:

- Page speed → higher task completion → better customer satisfaction
- Parts fill rate → faster maintenance TAT → higher mission-capable rate

### Quick Test: Is it Leading or Lagging?

- Causality: Does it plausibly cause the outcome? → Leading
- Controllability: Can we move it this sprint? → Leading
- Latency: Will it respond fast enough to steer? → Leading
- Confirmation: Is it the proof that outcomes changed? → Lagging
- Decision-use: Would we act on it before the outcome shows up? → Leading

> You need **both**: lead to steer; lag to prove.

### Examples by context

#### Healthcare / VA Programs

| Metric                         | Role    | Why it matters                |
| ------------------------------ | ------- | ----------------------------- |
| % Complete & Accurate med list | Leading | Enables safe care & adherence |
| Refill reminder reach/CTR      | Leading | Drives pickup → adherence     |
| Time-to-appointment            | Leading | Access drives outcomes        |
| 30-day medication adherence    | Lagging | Confirms behavior change      |
| 30-day readmission rate        | Lagging | Clinical outcome confirmation |

#### Department of State

| Metric                        | Role    | Why it matters                    |
| ----------------------------- | ------- | --------------------------------- |
| Application completeness rate | Leading | Reduces rework → on-time delivery |
| Interview-slot availability   | Leading | Drives visa wait times            |
| Passports delivered on-time   | Lagging | Citizen service outcome proof     |

#### Delivery & Performance Mix

| Metric                     | Role    | Why it matters                                   |
| -------------------------- | ------- | ------------------------------------------------ |
| Page load p95              | Leading | Faster pages → higher conversion/task completion |
| Feature adoption (%)       | Leading | Predicts retention/revenue after a delay         |
| DAU/MAU stickiness         | Leading | Habit strength → future retention                |
| Change Failure Rate (DORA) | Leading | Predicts incident volume/quality risk            |
| MTTR                       | Lagging | Confirms recovery performance after incidents    |
| Retention @ 90 days        | Lagging | Proof of durable value                           |
| NPS/CSAT                   | Lagging | Summative signal after experience                |

## How do we do it?

Our approach borrows from the best of modern product and platform thinking:

### **1. Identify What Matters**
We collaborate with stakeholders to define the outcomes in production that matter most — those are tied to user goals, delivery health, and business/mission value. These include:

#### Draft a metric tree

Confirm what Mission Impact looks like → Align on OMMTM → Limit to no more than five Leading & Lagging KPIs

#### Example OMMTM

- **Healthcare**: Deaths caused by treatement failures, patient safety indicator, readmission rates, medication adherence rate, and infection rates
- **Department of State**: Passports delivered on-time, visa interview access, crisis accountability speed, and digital self-service
- **United States Air Force**: Mission-capable rate, sorties, generate rate, and sensor-to-shooter timeline
- **United States Space Force**: on-orbit mission availability, custody time for resident space objects, and sensory-to-action latency

#### Example Delivery Health Metrics

- **DORA**

    - Deployment Frequency: how often you deploy.
    - Lead Time for Changes: code commit → running in prod.
    - Change Failure Rate: % of deployments that cause incidents/rollbacks.
    - Time to Restore Service (MTTR): time to recover from a failure.

- **Flow**

    - Lead Time: time from commitment to “done.”
    - Cycle Time: time from “started” to “done.”
    - Throughput: completed work items per time period.
    - Work in Progress (WIP): count of items currently in flight.
    - Work Item Aging: how long an in-progress item has been open.

- **Quality**

    - Escaped Defects or Defect Rate: defects found after release (often by severity; complementary to DORA).

- **Planning & Predictability**

    - Velocity: completed story points per sprint (use for team-internal forecasting only).
    - Sprint Burndown: remaining work vs. time inside the sprint.
    - Epic/Release Burn-up/Down: progress toward a larger goal over multiple sprints.

#### Example User, Usage and Performance/Reliability Metrics

- **Users (Who are they? Do they stay?)**

    - New Users: First-time users in given period.
    - Active Users (DAU/WAU/MAU) Users with one or more meaningful event in timeframe.
    - Activation Rate: New users reaching first value milestone.
    - Churn Rate: Users inactive beyond threshold.
 
- **Usage (How often? How deep? How broad?)**

    - Sessions/User: Avg sessions per active user.
    - Events/Session: Avg meaningful actions per session.
    - Feature Adoption: Unique users who used feature x.
    - Task Completion Rate: Users completing task without help.
    - Funnel Conversion: Step-to-step percetnage drop-offs.

- **Performance/Reliability**

    - Availability/Uptime: Percetnage of time service meets Service Level Objective (SLO).
    - Latency: Response time distribution.
    - Error Rate: Failed requests over total number of requests.
    - Crash Rate: Crashes per session, over total number of users



### **2. Start with Questions**
Before jumping into dashboards or automation, we begin by asking:
- What behavior change do we want to see in users?
- What mission impact are we hoping to achieve?
- What assumptions are we trying to validate?

These questions help us frame our data needs around real-world outcomes. Early on, we often track these metrics manually or with simple tools — spreadsheets, surveys, observation — so we can quickly learn what matters. If a low-fidelity solution helps us assess outcomes in prod, we start there. Then, once we’ve validated what’s important, we invest in automation for greater speed and scale.

### **3. Instrument & Automate**
We lean on tools like Prometheus, Grafana, and feature flag analytics to automate collection where feasible. This reduces manual burden and ensures we capture high-fidelity data in near-real time.

### **4. Analyze & Share**
Data isn’t useful until it’s interpreted. We visualize and review metrics weekly, monthly, and at key product moments (launches, pivots, retros). Dashboards and reports are made accessible to stakeholders to drive shared understanding and accountability.

### **5. Continuously Improve**
We don’t treat our metrics as static. As our products evolve, so do the questions we ask. Every iteration is an opportunity to refine how we measure success — and to stop measuring what no longer matters.

---

Want to get better at defining the right metrics for your product or service? Start with this question:  
***“What is the smallest amount of measurable learning, that shows we’re heading in the right direction for mission impact?”***

Then test, learn, and adapt — just like we do with everything else.


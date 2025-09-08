# Rate and Ratio Metrics
*The ideal way to measure success as changes are introduced*

---

## What are Rate and Ratio Metrics?

Rate and ratio-based metrics both compare two numbers through division, but the distinction lies in the relationship between the quantities and the role of time. A rate metric explicitly measures a change over time, while a ratio metric compares two quantities that can be of different units and do not necessarily involve time.

### Why Delivery Teams use them

#### Apples-to-apples comparability

Normalizing by exposure (time, users, assets, $$) removes scale effects.
> Example: 500 errors with 50M requests (0.01 per 1k) is far better than 50 errors with 10k requests (5 per 1k).

#### Fair performance signals

Rates/ratios separate effort/scale from quality/effectiveness so teams with different sizes can be compared fairly.
> Example: Sorties per aircraft-day, interviews per adjudicator-day, incidents per 1k users.

#### Decision-ready levers

Every rate = numerator ÷ denominator → two levers to pull. You can ask “do we fix quality (numerator) or increase capacity (denominator)?”
> Example: On-time % can improve by reducing delays or by better intake completeness to shrink rework.

#### Forecasting & capacity planning

Rates are plug-and-play for projections.
>Example: Throughput per FTE-day × staffed FTE-days ⇒ next sprint’s delivery forecast.

#### Experiment & attribution clarity

Ratios (conversion, adherence, success %) and rates (per user/week) are robust to traffic swings, making A/B testing results interpretable and comparable across cohorts.

#### Benchmarking & SLOs

You set thresholds on normalized scales (e.g., p95 latency, <1 change failure per 20 deploys, >95% on-time). This ties directly to policy and user promises.

#### Executive storytelling

Ratios collapse complexity into a single, stable idea (e.g., “9.7 readmissions per 1,000 discharges”). It’s easy to compare over time or against peers.

## What's the difference between rate and ratio metrics?

### Rate-based Metrics

A rate measures the frequency of an event over a specific time period. It describes how one quantity changes in relation to another, with time as a critical component. Rates often answer the question, "how often is something happening?". So think of this metric as events per unit of exposure (time, people, assets, miles, $$). 

> Incidents per 1,000 users, per week

#### Rate Mini Template

```
name: <metric name>
formula: numerator / exposure × K
numerator: <event count or amount>
exposure: <time, users, assets, $…>
K (scaling): <1, 100, 1,000…>
window: <e.g., weekly, rolling 7d>
notes: zero-denominator rule, stratifications, owner
```

#### Rate Metric Characteristics

* The denominator is a unit of time, such as seconds, hours, or years.
* It quantifies a dynamic process, flow, or speed.
* The comparison is between two quantities with different units of measure. 

#### Example Rate Metrics

* Heart rate: Beats per minute.
* Website traffic: Requests per second.
* Speed: Miles per hour.
* Birth rate: Births per 1,000 people per year.
* Conversion rate: Percentage of users who complete a desired action, like a purchase, within a given period. 

### Ratio-based metrics

A ratio is a metric that compares two numbers or aggregations to show their relationship. Unlike rates, the denominator is not necessarily a unit of time and can be customized to align with specific business needs. Ratios help to normalize data and provide more nuanced insights into performance. So think of this metric as ***(success or failure dataset ÷ total opportunities) * 100*** 

> On-time passports ÷ all passports = on-time %

#### Ratio Mini Template

```
name: <metric name>
formula: numerator / denominator × 100
numerator: <what counts as “success”>
denominator: <opportunity set>
window: <e.g., trailing 28 days>
notes: exclusions, min denominator N, owner
```

#### Ratio Metric Characteristics

* The denominator is a user-defined quantity, such as accounts, orders, or another event.
* It can compare quantities with the same or different units.
* Ratios normalize data to provide a fairer comparison between different groups or time periods. 

#### Example Ratio Metrics

* Average Order Value (AOV): Total revenue divided by the number of orders. This provides a more meaningful comparison than simply looking at total revenue, especially if the number of orders fluctuates.
* Revenue per add-to-cart click: Total revenue from purchases divided by the number of clicks on the "add to cart" button. This measures the efficiency of the cart addition process.
* Average revenue per paying user (ARPPU): Total revenue divided by the number of paying users. This metric excludes non-paying users from the calculation.
* Feature adoption per account: Total uses of a feature divided by the number of accounts. For B2B software, this can be more insightful than feature adoption per user, which might be skewed by a high number of users at a single account.

### Key Differences and Interpretations

| Aspect        | Rate                                                                    | Ratio                                                                                       |
|---------------|-------------------------------------------------------------------------|---------------------------------------------------------------------------------------------|
| Denominator   | A unit of time (e.g., per second, per year)                             | A user-defined quantity (e.g., per account, per order)                                      |
| Purpose       | To measure the frequency, speed, or occurrence of an event over time    | To compare the relationship between two quantities for normalization or efficiency analysis | 
| Use Case      | Tracking trends in dynamic processes like website requests or mortality | Analyzing efficiency metrics like revenue generation or feature engagement                  | 
| Interpreation | How quickly or often something happens                                  | How one number relates to another, providing context and normalization                      | 

### How to use them well

* **Always show the denominator.** Publish numerator / denominator × K in the definition.
* **Pick the right exposure.** Time, users at risk, attempts, assets, or size (KLOC, $, miles).
* **Use rolling windows** (e.g., trailing 28d) to reduce seasonality noise.
* **Aggregate from sums, not averages.** Compute Σnumerators / Σdenominators across segments.
* **Guard against tiny denominators.** Set a minimum N before reporting or alerting.
* **Pair rates with counts.** A small rate change on massive volume can be mission-critical.

### Five denominator patterns

| Pattern                                 | Denominator (exposure)                                                   | Formula template                      | Example metrics                                                                         | When to use / Notes                                                                           |
| --------------------------------------- | ------------------------------------------------------------------------ | ------------------------------------- | --------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------- |
| **1) Time exposure**                    | Time window (hours, days, weeks)                                         | `rate = events / time_window × K`     | Errors/day; Deploys/week; Tickets/hour                                                  | Great for tempo/throughput. Use rolling windows (e.g., trailing 7/28d) to smooth seasonality. |
| **2) Population at risk / Users**       | Active users / people at risk in window                                  | `rate = events / active_users × K`    | Incidents per 1k users; Help tickets per 100 employees; Security alerts per 10k devices | Fair comparisons across different user counts. Define “active/at risk” precisely.             |
| **3) Opportunity set**                  | Attempts / eligible items                                                | `ratio = successes / opportunities`   | Conversion %; On-time %; Test pass rate                                                 | Best for effectiveness. Ensure numerator ⊆ denominator and eligibility is stable.             |
| **4) Asset / capacity units**           | Asset exposure (aircraft-days, server-hours, adjudicator-days, FTE-days) | `rate = outputs / asset_exposure`     | Sorties per aircraft-day; Requests per server-hour; Interviews per adjudicator-day      | For productivity/utilization. Align asset time with operating hours, not calendar.            |
| **5) Size / work / cost normalization** | Size of work (KLOC, GB, miles, transactions, \$)                         | `metric_per_unit = amount / size × K` | Defects per KLOC; Cost per transaction; Energy per GB                                   | For density/unit economics. Watch for case-mix differences as size grows.                     |

#### Notes

* ***K*** is a readability scaler (e.g., ×100 for %, ×1,000 for “per 1k”).
* Aggregate across segments with sums, not averages: Σnumerators / Σdenominators (avoid averaging percentages).
* Always publish the exact definition (numerator, denominator, window, exclusions) with an owner and a change log.

### Picking the right denominator

| If your question is…               | Use this denominator                                   |
| ---------------------------------- | ------------------------------------------------------ |
| “How often over time?”             | Time window (hours/days/weeks)                         |
| “How common among users?”          | Active users / population at risk                      |
| “How effective out of tries?”      | Eligible attempts / opportunities                      |
| “How productive are assets/teams?” | Asset-exposure (aircraft-days, server-hours, FTE-days) |
| “How dense relative to size?”      | Size measure (KLOC, GB, miles, \$)                     |

### Mini-examples by domain

| Domain              | Metric                                    | Type       | Formula (windowed)                                                       | Example Unit/Scale       | Notes                                                    |
| ------------------- | ----------------------------------------- | ---------- | ------------------------------------------------------------------------ | ------------------------ | -------------------------------------------------------- |
| Product / Software  | Error rate                                | Rate       | `errors_per_1k = (error_requests / total_requests) × 1_000`              | errors per 1k requests   | Normalize by requests for fair comparison.               |
| Product / Software  | Crash-free sessions                       | Proportion | `crash_free = 1 − (crashed_sessions / total_sessions)`                   | %                        | Higher is better; pair with crash count.                 |
| Product / Software  | Throughput                                | Rate       | `throughput = completed_items / elapsed_time`                            | items per day/week       | Compute from totals; **don’t** use `1 / avg_cycle_time`. |
| Department of State | On-time passport                          | Proportion | `on_time_pct = on_time_deliveries / all_deliveries`                      | %                        | Define service standard window explicitly.               |
| Department of State | Interviews per adjudicator-day            | Rate       | `interviews_per_adjudicator_day = interviews / Σ(adjudicator_work_days)` | interviews per day       | Use **work** days, not calendar days.                    |
| Department of State | Visa no-show                              | Proportion | `no_show_pct = no_shows / scheduled_interviews`                          | %                        | Track by post and appointment type.                      |
| U.S. Air Force      | Sorties per aircraft-day (SGR)            | Rate       | `SGR = sorties / Σ(aircraft_possessed_days)`                             | sorties per aircraft-day | Align exposure to **possessed/available** days.          |
| U.S. Air Force      | Maintenance findings per 100 flight hours | Rate       | `findings_per_100_fh = findings / flight_hours × 100`                    | per 100 FH               | Good for reliability density.                            |
| U.S. Space Force    | Conjunction alerts                        | Rate       | `alerts_per_10k = alerts / (tracked_objects × weeks) × 10_000`           | alerts per 10k objs/wk   | Normalizes by catalog size and time.                     |
| U.S. Space Force    | Custody ratio                             | Proportion | `custody_pct = custody_time / total_time`                                | %                        | Also track reacquire time (p50/p90).                     |
| Healthcare / VA     | 30-day medication adherence               | Proportion | `adherent_pct = adherent_patients / eligible_patients`                   | %                        | Define eligibility & lookback precisely.                 |
| Healthcare / VA     | Readmissions                              | Rate       | `readmit_per_1k = readmissions / discharges × 1_000`                     | per 1k discharges        | Pair with severity/case-mix stratification.              |

### Misleading signals to monitor

#### 1) Context

When interpreting both rate and ratio metrics, it is important to consider the context of the underlying numbers. For example, "revenue per visit" might improve simply because the number of visits has decreased, not because the revenue per user has increased. Always examine the component metrics (the numerator and denominator) to understand what is driving the change. 

#### 2) Denominator Drift / Case-Mix Changes

Imagine two jars of jellybeans: big beans and tiny beans. You taste a few from each jar and both taste yummier than last time. But today you scooped way more tiny beans into your bowl than big ones. Your bowl now tastes less yummy overall—even though each jar got yummier. The mix changed.

> **What goes wrong:**
Rates are “thing per something.” If the “per something” (the denominator) changes a lot—more low-conversion traffic, more hard cases, a different region—your overall rate can go up or down just because the mix changed, not because you got better or worse.

Fixes to consider (pick 2 to 3):

* **Compare like with like:** Break the metric into slices (by region, device, severity). Trend each slice.
* **Publish the mix:** Show a small table: segment %, segment rate.
* **Recompute from sums:** Use Σnumerators / Σdenominators for rollups - don't average percentages.
* **Pin the denominator:** When possible, keep the “at risk” group definition stable over time.

#### 3) Gaming (moving the number without real progress)

Your chore score is “toys put away per minute.” You want a gold star, so you count only tiny toys and stop the timer early. Number looks great; the room is still messy.

> **What goes wrong:**
People optimize the formula, not the outcome: narrowing eligibility, skipping hard cases, redefining “done,” or timing windows to look good.

Fixes to consider (guardrails + governance):

* **Lock definitions:** Numerator, denominator, window, exclusions—versioned with a change log.
* **Add guardrails:** Pair the KPI with quality/safety checks (e.g., accessibility ≥95%, no severity-1 incidents).
* **Audit edge cases:** Sample items just below/above thresholds.
* **Balance the portfolio:** Use 3–7 inputs that push in different directions so one can’t be gamed without another flashing red.

#### 4) Over-normalization (ratios hide real people or cost)

“99% of kids got lunch” sounds amazing—until you hear there are a million kids. That missing 1% is 10,000 hungry kids.

> **What goes wrong:**
Beautiful rates can mask big absolute numbers (or tiny ones that don’t matter). Leaders need both the rate and the raw count.

Fixes to consider (apply the always show both rule)

* **Publish pairs:** “On-time = 96% (48,000/50,000).”
* **Add thresholds in counts:** “No more than 50 severe incidents / month” and “<0.1 per 1k users.”
* **Escalate big absolutes:** Create alerts when the count crosses a mission-meaningful line, even if the rate is fine.

#### 5) Seasonality

In Florida summers, the sky makes afternoon lightning almost every day. If you only look at calm months (October–April), you’ll think “We almost never get weather alerts!” Then June shows up with daily thunderstorms and you panic. It’s not that the team got worse—it’s summer storm season.

> **What goes wrong:**
If you baseline your “weather holds per week” or “scrubs due to weather” using October–April, you’ll set targets that are too optimistic for May–September. You’ll trigger false alarms, overreact, and misjudge performance. (Hurricane season June–November adds more spikes.)

Fixes to consider: 

* **Seasonal baselines:** Keep two bands:
    
    * **Wet/convective season:** May–September (daily sea-breeze storms; frequent lightning alerts).
    * Drier season:** October–April (fewer lightning alerts; different wind/ceiling patterns).

* **Compare like with like:**
    
    * **Month-over-month YoY** (July this year vs. July last year), not July vs. January.
    * **Same time-of-day windows** (morning vs. afternoon launches) since storms peak in afternoons.

* **Rolling windows:** Show trailing 28/84-day rates to smooth noisy bursts from storm clusters or tropical systems.
    
* **Weather-adjusted rates:** Normalize by exposure to weather, e.g.:

> scrubs_per_10_lightning_alert_days = scrubs / lightning_alert_days × 10
> holds_per_100_operating_hours_in_alert = holds / hours_under_alert × 100

* **Annotated dashboards:** Mark known seasonal drivers: sea-breeze thunderstorm season (May–Sep), hurricane season (Jun–Nov), major front passages, range maintenance windows.
* **Capacity & scheduling:** Bias critical ops toward morning windows in summer; pre-plan extra buffer days May–September.

#### 6) Scope alignment

You count red blocks in the jar, but then you divide by all blocks in the room. That’s mixing jars and rooms—your math is confused.

> **What goes wrong:**
The numerator and denominator don’t describe the same set (product, region, device, time window, eligibility). You get a pretty number that doesn’t mean anything true.

Fixes to consider:

* **Same filters, always:** Numerator ⊆ Denominator with identical product/region/device/time filters.
* **One definition card:** Every KPI has a definition with numerator, denominator, window, exclusions, owner.
* **SQL sanity checks:** Unit tests—if you sum segment rates weighted by segment denominators, you get the overall rate.
* **Eligibility first:** Define who’s in the game before counting wins (e.g., “eligible users” vs. “all users”).
* **Version & lock:** Treat KPI definitions like code; change log any tweak.

#### 7) Stratify critical KPIs

Your class average is an A, yay! But some kids are quietly failing. Looking only at the average hides who needs help.

> **What goes wrong:**
The overall number hides gaps. Some groups (device types, regions, priority users, equity segments) have very different results. You celebrate the average and miss the pain.

Fixes to consider:

* **Standard slice set:** Always break key KPIs by priority (P1 vs P3), device (iOS/Android/Web), region/site, new vs. returning, and equity (e.g., accessibility or underserved groups).
* **Parity checks:** Add gap thresholds (e.g., any segment >X pts worse than overall = alert).
* **Small-N rules:** Suppress or aggregate tiny segments to avoid noisy or identifying data.
* **Segment owners:** Name an owner for each critical segment (who acts when it’s red).
* **Dash default:** Show overall + top 3 worst segments by default—don’t hide them behind clicks.

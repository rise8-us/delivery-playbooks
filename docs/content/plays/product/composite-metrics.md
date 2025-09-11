# Composite Metrics
*The way to measure success when you need to assess multiple contributing factors*

---

## What are Composite Metrics?

Have you ever encountered a situation where your team couldn't agree on, or it wasn't right to, prioritize just one metric as the One Mission Metric That Mattered (OMMTM)? A **composite metric** (a.k.a. **index** or **score**) is a ***single number*** created by ***combining multiple indicators***—often after normalizing them to the same scale and weighting them. It’s useful when no single metric captures the outcome you care about (e.g., “readiness,” “service quality,” “data health”).

> Think: *one* score that summarizes several signals you don’t want to inspect one-by-one.

## When to use (and when not to)

### Use when:

* The outcome is multidimensional (quality and speed and safety).
* You need a single decision lever for prioritization or incentives.
* You want a stable, auditably-defined “north star” that blends inputs.

### Avoid when:

* One metric clearly dominates (e.g., “on-time passports”).
* The composite would hide trade-offs you must see (safety vs. speed).
* You’d set incentives that can be gamed by over-optimizing one part.

## How to build a good composite (5 steps)

1. **Select components** (3–5 max). Align on why each matter, and they must be independently measurable.
2. **Normalize** to resize numbers, so that everything fits on a common 0–1 scale:
    * If higher-result-is-better: n = clamp(value / target, 0, 1)
    * If lower-result-is-better: n = clamp(target / value, 0, 1)
    * Bounded % results already support a 0–1 scale: maybe cap tails.
    * ***"Clamp"*** keeps the result inside the ruler (never below 0 or above 1)
    * Once everything is on 0–1, you can average or weight them fairly.
3. **Weight** importance of each component, where the sum of each weight = 1
    * Keep weights simple
    * Either equal weights, or multiples of 10 (e.g. 50/30/20)
4. **Aggregate** with an appropriate function:
    * Compensatory (i.e. trade-offs are allowed): Score = Σ (wᵢ × nᵢ) (*i.e. sume of weights x scores*)
    * Non-compensatory (no hiding failures): either through min(nᵢ) (*i.e. weakest link wins*), or geometric mean Π nᵢ^{wᵢ} (*i.e. multiply each component by its weighting*)
    * Add penalties/gates: if any critical nᵢ < threshold, cap the score.
5. **Govern**: versioned definition, owners, review cadence, change log, back-tests, sensitivity checks (does a small change in one input swing the score too much?).

### How normalizing common 0-1 scales work

#### When higher result is better (e.g. uptime, NPS, on-time%)

***The formula n = clamp(value / target, 0, 1)*** translates to, "how close are we to the target?"

* If value = target → n = 1
* If value is half the target → n = 0.5
* If value exceeds target → n sticks at 1

##### Tiny example:

value 0.88 (88%), target 0.95 (95%) → 0.88/0.95 = 0.926 → 0.926

##### Sheets/Excel:

```
=MIN(MAX(B2/C2, 0), 1)
(Assume B2 = value, C2 = target)
``` 

#### When lower result is better (e.g. latency, cost, lead time, processing time)

***The formula n = clamp(target / value, 0, 1)*** translates to, "how close am I to being at or below the target?"

* If value = target → n = 1
* If value is double the target → n = 0.5
* If value drops below target → n caps at 1

##### Tiny example:

value 22 days, target 14 days → 14/22 = 0.636 → 0.636

##### Sheets/Excel:

```
=MIN(MAX(C2/B2, 0), 1)
(B2 = value, C2 = target)
``` 

#### Common gotchas and fixes

* **Percent already 0–1?** You can use it directly, or divide by the target if you want “% of target” (then clamp).
* **Target = 0?** Don’t divide by 0. Pick a realistic small target or use a different normalization.
* **Noisy zeros/near-zeros?** Consider a tiny floor (e.g., MAX(n, 0.05)) only if that aligns with policy; otherwise use explicit gates (e.g., “if accessibility <95%, cap the score”).
* **Document everything:** Numerator, denominator, window, target, exact formula, owner, and a change log.

### How aggregates with an appropriate function works

#### Compensatory (trade-offs allowed)

Like a school GPA. A great grade in one subject can make up for a weaker grade in another. You’re averaging, but giving some parts more weight. Use this approach when you’re OK with trade-offs and you want a clear, explainable score.

##### Tiny example:

* Components (already on a 0–1 scale): A=0.90, B=0.60, C=0.80
* Weights: A 50%, B 30%, C 20%
* Score = 0.5×0.90 + 0.3×0.60 + 0.2×0.80 = 0.79 (79/100)

##### Sheets/Excel:

```
=SUMPRODUCT(weights_range, scores_range)
```

#### Non-compensatory (no hiding failures)

Leverage non-compensatory aggregate functions when all parts of the composite metric ***must be strong together*** and you don't want one star performer to hide a laggard. When monitoring for a critical "weakest link" in our composite result, if any part is low, the whole score is that low. So use this approach when any single failure should drag the whole score down (e.g., safety must be OK everywhere). When we want to ensure we have a balance in our composite result—like a recipe—if one ingredient is missing, the dish suffers a lot. A geometric mean approach rewards balance, and penalizes weak links more than a simple average. The extra punishment from Geometric means may mislead decision-making on low component scores, so brief anomolies or situations that are truly outside of your control, teams should only use geometric means when the following are true. When dealing with seasonality, teams should consider longer test cycles to confirm sustained performance over time.  

* Components are complementary and you want balanced performance (i.e. no one metric should dominate).
* All components are strictly positive and well measured on a stable 0-1 scale.
* You want weak links to be penalized more than a sum would (e.g. reliability score blending uptime, latency and error rate).

##### Tiny example:

* A=0.90, B=0.60, C=0.80 (weights 0.5/0.3/0.2)
* **Min**: min = 0.60
* **Geometric mean**: ≈ 0.778 (a bit lower than the 0.79 average because B is weak)

##### Sheets/Excel:

```
=EXP(SUMPRODUCT(weights_range, LN(scores_range)))
(Scores must be > 0.)
```

#### Penalties/Gates (must-pass rules)

Rule: “If any critical part is below a bar, cap the whole score.” Using a driver's test analogy, you can ace parking and signaling, but if you run a red light, you fail—no amount of other goodness can fully compensate.

##### Tiny example:

* Add non-compensatory gate for critical standards or sacred dimensions (e.g. safety, accessibility)
* "If accessibility < 95%, cap the result at 0.60"

##### Sheets/Excel:

```
=IF(MIN(critical_range) < threshold, cap_value, overall_score)
```

#### Side-by-side intuition (same data)

| Method                            | What it “feels” like       | Result with A=0.90, B=0.60, C=0.80 (w=50/30/20) |
| --------------------------------- | -------------------------- | ----------------------------------------------- |
| Compensatory (weighted average)   | **GPA**—trade-offs allowed | **0.79**                                        |
| Geometric mean (non-compensatory) | **Recipe**—balance matters | **≈ 0.778**                                     |
| Minimum (non-compensatory)        | **Weakest link**           | **0.60**                                        |
| Gate (policy rule)                | **Must-pass test**         | e.g., “cap at 0.60 if Accessibility < 0.95”     |

> If one part tanks (A=0.90, ***B=0.20***, C=0.80):
> * Weighted average → 0.67 (still decent)
> * Geometric mean → ≈ 0.56 (harsher)
> * Minimum → 0.20 (shows the failure)

#### When to choose which aggregate function

* **Need simplicity and buy-in?** → Compensatory (weighted average)
* **Need balance across all parts?** → Geometric mean
* **Some criteria are sacred (safety, accessibility)?** → Use gates (non-compensatory), not just Geometric mean

#### Bottom Line

Don’t always default to geometric mean. Choose the aggregation that matches your incentives and policy:

* Use weighted sum + explicit gates for clarity and governance.
* Use geometric mean when balanced, all-around performance is truly essential and your components are stable, positive, and well-normalized.
* Always show the component metrics alongside the composite, and version the definition (weights and gates) with a change log.

## Hihgh-level example

**Goal:** “Service Quality Score” combining speed, success, and satisfaction.

* Components (targets):
    * On-time completion rate (target 95%) → n1 = on_time (already 0–1)
    * Median time to complete (lower is better; target 2 days) → n2 = min(1, 2 / median_days)
    * CSAT 1–5 (target 4.5) → n3 = min(1, csat / 4.5)
* Weights: equal (1/3 each)
* Compensatory sum: Score = (n1 + n2 + n3)/3
* Non-compensatory option: Score = (n1 × n2 × n3)^(1/3) and gate: if on_time < 0.85, cap Score at 0.6.

## Citizen Sevice Index Example

**Goal:** one score that summarizes citizen service quality by blending speed, success, satisfaction, and accessibility.

### 1. Definitions (what we’ll calculate)

**Four components & targets:**

1. On-time completion (% of passports delivered within standard). (Higher is better; already 0–1.)
2. Appointment speed (median days to interview). (Lower is better; target = 14 days.)
3. CSAT (1–5). (Higher is better; target = 4.5.)
4. Accessibility conformance (% of pages passing required checks). (Higher is better; already 0–1.)

**Normalization (put everything on 0–1 scale):**

* Higher-is-better: n = clamp(value / target, 0, 1) (for percent/ratio with a target ≤ 1, this may already be 0–1)
* Lower-is-better: n = clamp(target / value, 0, 1)

**Weights (sum to 1):**

* On-time 0.35 | Appointment speed 0.25 | CSAT 0.25 | Accessibility 0.15

**Aggregation:** 

* weighted sum → Index = Σ(weight × normalized_value)

**Gate (non-negotiable quality rule):** 

* If Accessibility < 0.95, cap the final score at 0.60 (i.e., you can’t earn an “A” if you fail accessibility).

<br/>

### 2. Sample data (Month A)

| Component                       | Raw value |                 Target | Direction |                Normalization (n) |
| ------------------------------- | --------: | ---------------------: | --------- | -------------------------------: |
| On-time completion              |       88% | 95% (informative only) | ↑         |           **0.88** (already 0–1) |
| Appointment speed (median days) |   22 days |                14 days | ↓         |   **0.636** = clamp(14/22, 0, 1) |
| CSAT (1–5)                      |       4.2 |                    4.5 | ↑         | **0.933** = clamp(4.2/4.5, 0, 1) |
| Accessibility                   |       97% |              95% (min) | ↑         |           **0.97** (already 0–1) |

#### Compute weighted contributions

| Component             | Weight |     n | Contribution = weight × n |
| --------------------- | -----: | ----: | ------------------------: |
| On-time               |   0.35 |  0.88 |                 **0.308** |
| Appointment speed     |   0.25 | 0.636 |                 **0.159** |
| CSAT                  |   0.25 | 0.933 |                 **0.233** |
| Accessibility         |   0.15 |  0.97 |                 **0.146** |
| **Total (raw index)** |        |       |                 **0.846** |

<br/>

Gate check: Accessibility = 0.97 ≥ 0.95 → no cap applied.
Final Index (Month A) = 0.846 → (84.6/100).

> **Result interpretation (Month A):** Appointment speed (0.636) is the weak link; improving median days will move the index fastest.

<br/>

### 3. What if we improve speed & cSAT, but slip on accessibility? (Month B)

| Component                       | Raw value |                 Target | Direction |                              Normalization (n) |
| ------------------------------- | --------: | ---------------------: | --------- | ---------------------------------------------: |
| On-time completion              |       94% | 95% (informative only) | ↑         |                                       **0.94** |
| Appointment speed (median days) |   12 days |                14 days | ↓         |   **1.000** = clamp(14/12, 0, 1) → capped at 1 |
| CSAT (1–5)                      |       4.6 |                    4.5 | ↑         | **1.000** = clamp(4.6/4.5, 0, 1) → capped at 1 |
| Accessibility                   |       93% |          **95% (min)** | ↑         |                                       **0.93** |

#### Weighted sum (before gate):

0.35×0.94 + 0.25×1.00 + 0.25×1.00 + 0.15×0.93 = 0.9685 → 96.85/100

Gate check: Accessibility = 0.93 < 0.95 → apply cap to maintain citizen equity/quality.
Final Index (Month B) = 0.60 (capped), not 0.9685.

> Result interpretation (Month B): Even with great speed and satisfaction, failing accessibility is unacceptable; the gate forces attention to this critical quality dimension.

<br/>

### 4. Why use a gate?

* A simple weighted sum is compensatory (great speed could hide poor accessibility).
* The gate makes the index non-compensatory on critical standards: certain failures must be fixed before you can score highly.

### 5. What if we want to punish weak links in our composite metric?

If you want the math itself to be less compensatory, use the geometric mean (still with the same 0–1 normals and weights). Geometric mean naturally down-weights any single weak link, making “all-around” performance matter more.

#### Citizen Service Index Example

* Formula = (n_on_time^0.35) × (n_speed^0.25) × (n_csat^0.25) × (n_access^0.15)
* Month A (0.88, 0.636, 0.933, 0.97) → ≈ 0.836 (vs 0.846 sum)
* Month B (0.94, 1.00, 1.00, 0.93) → ≈ 0.968 before gate → 0.60 after gate

<br/>

### 6. How to act on this composite result

* Move the index by attacking the lowest normalized component first (fastest gain).
* Always review the component trend lines alongside the single score (avoid masking).
* Keep the definition versioned (weights, targets, formula) with owners and a change log.

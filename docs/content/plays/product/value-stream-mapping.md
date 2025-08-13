# Value Stream Mapping (VSM)
*A Strategic Guide for Grasping Current State and Accelerating Mission Impact*

---

## What is Value Stream Mapping?

Value Stream Mapping (VSM) is a Lean tool used to visualize the flow of work, materials, and information needed to deliver value to a customer—from request to delivery. In software delivery, this means mapping everything from a user need to production deployment.

At Rise8, we use VSM in relation to Theories of Constraints to draw focus to identifying and removing constraints that limit throughput, and thus increasing manufacturing capacity. By revealing how value flows through our system, highlighting inefficiencies, and aligning teams around transformation priorities we create imbalances to maximize throughput at the constraint. 

- **Every system has a constraint:** This is the factor that most restricts the system's output.
- **Constraints set the pace:** Draw focus to the constraint until it is no longer the constraint
- **Improving the constraint improves the system:** Focusing efforts on the constraint yields the most significant performance enhancements.
- **Continuous improvement:** Once a constraint is resolved, another will emerge, necessitating ongoing attention and refinement.

### Why is Value Stream Mapping valuable?

To visualize and improve our process of delivering greater value to customers, we follow seven key principles for Value Stream Mapping:

1. **Customer-Centric Focus:** VSM should always begin with the customer in mind. Understanding what the customer values ensures that the mapping process aligns with delivering that value efficiently.
2. **Holistic Systems Thinking:** Rather than optimizing individual processes, VSM emphasizes viewing the entire value stream to identify and eliminate waste, ensuring improvements benefit the whole system.
3. **Leadership Engagement:** Effective VSM requires the involvement of stakeholders who have the authority and vision to implement significant changes. Their engagement ensures that improvements are strategic and aligned with mission objectives.
4. **Distinction Between Core and Supportive Value Streams:** Both core value streams (directly delivering products or services) and supportive value streams (such as employee onboarding or software delivery) are crucial for overall organizational performance.
5. **Data-Driven Analysis:** VSM relies on collecting accurate data for process times, lead times, and other metrics that are relevant to your mission/business process to identify bottlenecks and areas for improvement.
6. **Visualization for Clarity:** Creating visual maps of processes helps teams understand current workflows, identify inefficiencies, and design improved future states.
7. **Iterative Improvement:** VSM is not a one-time activity. Organizations should regularly revisit and update their value stream maps to reflect changes and continue improving.

> *"VSM gives us the lens to diagnose noise in delivery and rewire teams for continuous value flow."*

### How do we categorize waste?

The following categories of waste are used by nearly all communities. We've provided some Software Delivery and Healthcare examples to help translate this into various contexts.

| Waste Category                                                                     | Software Delivery Example                                              | Healthcare Example                                                      |
|------------------------------------------------------------------------------------|------------------------------------------------------------------------|-------------------------------------------------------------------------|
| **Defects:** products or services requiring rework due to errors or non-conformity | Bugs in production causing hotfixes or patches                         | Misdiagnoses or medication errors requiring correction                  |
| **Overproduction:** making more than required or before needed                     | Developing extra features that go unused by end-users                  | Conducting unnecessary diagnostic tests or preparing surplus supplies   |
| **Overprocessing:** doing more work than the customer needs or expects             | Extra documentation or rework due to unclear requirements              | Duplicate paperwork or redundant procedural steps                       |
| **Waiting:** idle time when processes or people wait for the next step             | Delays waiting for code reviews, QA, or deployment approvals           | Patients waiting for test results, physician availability, or beds      |
| **Inventory:** excess materials or work-in-progress not yet adding value           | Backlog of unfinished code or features (WIP)                           | Stockpiling supplies or medications that risk expiration                |
| **Transportation:** unnecessary movement of materials or information               | Excessive handoffs between teams or environments                       | Moving patients between departments more than needed                    |
| **Motion:** unnecessary movement by people or equipment                            | Frequent context switching between tasks                               | Staff walking long distances to fetch equipment or records              |
| **Unused Talent:** under-utilizing employees’ skills, creativity, or knowledge     | Developers limited by bureaucracy and not tapped for improvement ideas | Staff ideas or advanced skills not leveraged for process improvements   |

<br/>

### What metrics are commonly used in VSM?

VSM metrics can span categories like time, flow, quality, cost, people, or any metric that is relevant to your mission context

| Metric Category             | Metric Name                                | Description                                                                                          | Software Delivery Example (Results)                       | Healthcare Example (Results)                                   |
|-----------------------------|--------------------------------------------|------------------------------------------------------------------------------------------------------|------------------------------------------------------------|----------------------------------------------------------------|
| **Time, Flow & Efficiency** | Lead Time (LT)                             | Time to complete an individual process step, as well as total time from order to delivery—reflects responsiveness of the process.                                | 5 days from ticket submission to production deploy         | 35 minutes from prescription request to fulfillment      |
|                             | Process Time (PT)                          | Time it takes between when the work arrives at a process step until it’s passed on to the next step, as well as total time spent executing all process steps (touch time).                                                   | 4 hours—actual coding, testing, and merging time per feature | 4 minutes—actual work in filling prescription          |
|                             | Throughput                                 | Rate at which units are delivered over time.                                                         | 3 features released per sprint                            | 20 prescriptions filled per hour                               |
|                             | Utilization                                | Percentage of time resources are in active use.                                                  | Developers active ~80% of day                             | Nurses spend ~70% shift on value-added patient tasks           |
|                             | Flow Efficiency                            | Ratio of processing time vs total lead time.                                                         | (4h PT ÷ 5 days LT) ≈ 3%                                  | (4 min PT ÷ 35 min LT) ≈ 11%                      |
| **Quality**                 | Defect Rate                                | Number or percentage of defect occurrences.                                                      | 10% bug rate found post-release                           | 2% medication dispensed incorrectly                            |
|                             | First Pass Yield                           | Share of units completed accurately without rework.                                                 | 85% of deployments succeed without hotfix                 | 90% of patient charts correct on first review                  |
|                             | Quality Filter Mapping                     | Percent of defects detected at each stage (e.g., dev, QA).                                          | Dev: 5%, QA: 3%, Prod: 2%                                 | Registration errors: 4%; Diagnostic errors: 6%                 |
|                             | % Complete & Accurate (%C&A)               | Share of work handed downstream with no issues.                                                     | 95% of code reviews pass without rework                   | 92% of patient charts are complete and accurate                |
|                             | Rolled %C&A                                | Overall downstream-ready rate across all steps (product of stepwise %C&A).                          | 0.95 × 0.90 × 0.92 ≈ 79% overall yield                    | 0.92 × 0.95 × 0.90 ≈ 79% across admission, assessment, care     |
|                             | Simple Avg %C&A                            | Unweighted average of %C&A across steps.                                                             | (95% + 90% + 92%) ÷ 3 ≈ 92.3%                             | (92% + 95% + 90%) ÷ 3 ≈ 92.3%                                 |
|                             | Weighted Avg %C&A                          | Average of %C&A weighted by volume at each step.                                                    | (95% × 50 + 90% × 30 + 92% × 20) ÷ 100 ≈ 92.1%            | (92% × 40 + 95% × 40 + 90% × 20) ÷ 100 ≈ 92.4%                 |
| **Cost**                    | Inventory Cost                             | Cost associated with holding WIP or stock.                                                          | $5,000 in backlog work-in-progress                       | $1,200 of unused medications in stock                        |
|                             | Waste Cost                                 | Estimated cost of inefficiencies or defects in the stream.                                          | $3,000 per sprint from bug-fix rework                    | $500 per week from patient flow delays                         |
| **Customer/Delivery**       | On-Time Delivery (%)                       | Percentage of units delivered by promised deadlines.                                                | 95% of features released on planned date                  | 90% of patients receive meds on schedule                       |
|                             | Customer Satisfaction                      | User-rated satisfaction.                                                                            | 4.5/5 from product surveys                                | 4.3/5 from patient feedback surveys                           |
| **Bottleneck Analysis**     | Relative Bottleneck Frequency              | How often a particular stage becomes a bottleneck.                                                     | Code reviews are bottleneck 60% of the time               | Lab results delay bottlenecks in 40% of patient flows         |
|                             | Relative Bottleneck Severity               | Degree of impact when a stage becomes a bottleneck.                                                            | Delays lead to +2 days release delay                     | Adds +30 min to patient wait time                             |
| **Mission**                 | One Mission Metric That Matters (OMMTM)    | The north star guiding metric, and any other critical KPIs that are relevant to the mission we're serving.                                            | Deployment Frequency (target on-demand) Lead Time for Changes (target less than one day) Change Failure Rate (target < 15%)        | Eliminate annual deaths caused by treatment failures (target = 0) |

<br/>

## Three Value Streams Relevant to Rise8's Business

Regardless of your role at Rise8, it's important to understand the three Value Streams that we influence, and how they support our company's value equation of optimizing for mission value:

1. **Customer Mission**: Represents personnel, capabilities and outcomes in production that impact real mission operations (e.g. running Air Operations Center missions such as Intelligence, Surveillance, and Reconnaisssance) 
2. **IT/Software Delivery**: Enables the delivery of mission capabilities, measured up through deployment into a production environment (e.g. enabling continuous delivery).
3. **Rise8 Delivery Service**: How we partner with customers to bridge the gap between output and impact by identifying opportunities for deploying elite software development for mission critical outcomes in production (e.g. deliver cloud & platform, apps & digital products as well as cybersecurity & RMF).

![Vakye Strans](../../../assets/vsm-types.png)

## Where VSM Fits in Our Continuous Improvement Framework

Value Stream Mapping is the **starting point** for understanding the current condition within the Improvement Kata framework:

1. **Understand the direction or challenge**  
   _What mission impact are we trying to enable?_
2. **Grasp the current condition**  
   _Use VSM to visualize the actual flow of value._
3. **Establish the next target condition**  
   _Set SMART goals based on constraints or opportunities identified._
4. **Experiment your way forward**  
   _Use this insight to conduct safe-to-fail experiments._

> *If you don’t know what value you're trying to achieve, how value is flowing, or what’s constraining it—start with a VSM.*

<br/>

## How to Facilitate a Value Stream Mapping Exercise

Try out our Figjam template [VSM Resources](https://www.figma.com/board/h6EfV3nAOHoAR9JOa7UXF7/-CREATE-COPY----Rise8-Standard-Delivery-Artifacts?node-id=0-1&p=f&t=y3WJv70v7goBSbmo-0) to facilitate current and target state VSM workshops, or assist in digitizing outputs from a workshop leveraging sticky notes. 

### Pre-Work Checklist

| Item | Why It’s Needed |
|------|-----------------|
| Clear mission objective | Guides what to optimize |
| Cross-functional participants | Ensures holistic view |
| Physical or virtual wall space | Allows collaborative mapping |
| Sticky notes or [Figjam board](https://www.figma.com/board/h6EfV3nAOHoAR9JOa7UXF7/-CREATE-COPY----Rise8-Standard-Delivery-Artifacts?node-id=0-1&p=f&t=y3WJv70v7goBSbmo-0) | Visual collaboration |
| Facilitation plan | Keeps session on track |
| Stopwatch or timer | Timebox conversations or measuring time performance of steps wihtin your VSM |

> *[Value Stream Mapping Supplemental Materials](https://tkmg.com/wp-content/files/VSM-Supplement.pdf) from Karen Martin & Mike Osterling.*

---

### Key Components to Map

| Component | Description |
|----------|-------------|
| **Mission Impact** | “What’s the core mission/business impact this value stream supports?” “How do we measure business/mission impact success today?” |
| **Trigger** | What kicks off the process? |
| **Supplier/Initiator** | Who starts the desired outcome of flow? |
| **Inputs** | What inputs are provided or required from initiators to drive our mission/business process? |
| **Customer/End-User** | Who receives our outputs, what do they do with it? |
| **Outputs** | What outputs do customers/end-users receive from our business/ mission process? |
| **Mission/Business Process Steps** | High level 'Value Added' 'Non-value Added' or 'Required Non-value Added' steps taken to deliver value |
| **Information/Material Flow** | Confirm how we move between steps in the value stream, and confirm if they're automated or manual transitions |
| **Tools** | Clarifying systems or artifacts used |
| **Metrics** | Align on what we need to measure for our value stream, how they'll be used to help make and validate decisions |
| **Handoffs** | Between people, systems, departments |
| **Pain Points** | Bottlenecks, delays, rework, rejections |

---

### Workshop Tips

💡 Ensure the right participants are invited to VSM workshops. Inviting the following personas will lead to better success:

- **Customer Leadership:** would be considered a leader of the government organization
- **Buyer:** responsible for making future contract decisions
- **Mission Owner:** represents the interests of the mission
- **Influencer:** someone who can advocate or dissuade leadership in the organization due to their experience or clout
- **User Community:** a leader, proxy, or member of the user base

💡 Start with your “Current State” value streams for the initial stream to be mapped.

💡 Focus on “Target State” once you have today’s streams mapped. Encourage participants to describe what really happens.

💡 Agree on refresh triggers/cycles (we recommend fitting this into your hypothesis validation steps, before starting a new hypothesis experiment)

💡 What to Avoid:

- Mapping discrete actor (systems or users) actions instead of flows
- Rushing straight to solutions
- Only soliciting contributions of a few people (only SMEs speaking)

---

### Facilitation Tips

💡 **Apply a “Go See and Find Out” mentality** – Encourage participants to describe what *really* happens, not what *should* happen.

💡 **Time-box mapping per stream** – e.g., conduct iterations of 60–90 minutes for mapping, 30 minutes for analysis, until you have enough clarity to make measurable decisions.

💡 **Ask probing questions** - What mission impact are we trying to enable? What causes delays here? Where do handoffs break down? Where do you wait on feedback? Where do we often repeat steps/work?

💡 **Avoid mapping wishful thinking** – It’s about the current state, not the ideal (this is more of a focus for Service Blueprint artifacts).

💡 There can be multiple initiators and end-users; A VSM can start & end with an end-user

💡 Steps should be high-level enough to demonstrate the overall process flow, but specific enough to be able to identify waste, hand-offs, and improvement areas. Examples:

- ❌ Too broad: Testing happens
- ✅ Just right: Lab tech runs blood test
- ❌ Too detailed: Lab tech labels the sample (we will get into deep, user-specific, behaviors with other artifacts)

---

### What to Avoid

- Mapping systems or roles instead of flows
- Rushing straight to solutions
- Over-scoping the stream (keep it narrow and meaningful)
- Failing to include voices from the edges (e.g., QA, Ops, Compliance)

---

<br/>

## Facilitation Script & Prescriptive Steps for Building a Current & Target State VSM

Use the following script and facilitation steps to confidently lead a Value Stream Mapping session. This structured approach ensures the session yields a high-quality map and actionable insights.

### Before the VSM Workshop

1. **Define the scope and objective**  
   _"We’re here to understand how value flows today—so we can unblock it and drive greater mission impact."_

2. **Identify the right participants**  
   Include frontline workers, key process owners, system leads, and stakeholders.

3. **Prepare the collaboration space**  
   Whether virtual or physical, have clear lanes for steps, time, pain points, actors, and tools.

4. **Send pre-read materials**  
   Share what a VSM is, why it matters, any existing VSM artifacts, and the session goals.

---

### During the Workshop

#### Opening Script (5 mins)
> _"Thanks for joining. Today we’re mapping our value stream to uncover where work gets stuck, who’s involved, and how it flows—or doesn’t flow—across systems and teams. This helps us deliver outcomes faster and with less pain. Our focus is on the **current state**, not what we wish it looked like."_

#### Step-by-Step Current State VSM Facilitation

1. **Establish the mission impact** - "What’s the core mission this stream supports?" (e.g., “Deliver approved benefits to Veterans”)
2. **Reaffirm known mission impact(s)** - “What’s the core mission/business impact this value stream supports?” “How do we measure business/mission impact success today?”
3. **Identify the initiator (supplier)** - “Who starts the desired outcome of the flow?”
4. **Identify the triggering event or inputs** - "What starts the process?" (e.g., “Veteran submits claim”)
5. **Identify end-user (customer)** - “Who realizes the desired outcome(s) of the flow?”
6. **Generate any outputs received by the customer** - "What outputs do customers/end-users receive from our business/ mission process?"
7. **Create the last mission/business process step** - "What is the last process step that delivers the desired outcome(s) to our custoemr and helps us achieve our mission impact(s)?"
8. **Create the initial mission/business process step** - "What is the first process step towards our desired outcome(s) + mission impact(s)?"
9. **Continue adding mission/business process steps** - "Is this next step value added, non-value added, or required non-value added?"
10. **Add flow context** - "Is flow automatically or manually pushed to the next mission/business process step?"
11. **Add actors to each step** - "Who or what does this work?"
12. **Identify tools/systems used** - "What tools support this step?"
13. **Mark handoffs and dependencies** - Use arrows to denote transitions or approvals.
14. **Estimate lead time and process time** - "How long does this take?"  "How long does it wait?"
15. **Capture pain points** - "Where do things break down?"  "What causes delay or rework?"  "What work gets kicked back?"
16. **Highlight visible and invisible work** - Surface shadow systems, workaround steps, manual interventions.
17. **Review the full map** - "What surprises you?"  "Where do we lose the most time or value?"
18. **Upon final walkthrough, capture questions and assumptions!** 

---

#### After the Current State VSM Session

1. **Document and digitize the map** - Use Figjam, Miro, Lucidchart, or Mural to clean up and archive.
2. **Synthesize insights** - Highlight biggest bottlenecks, gaps, silos, questions and assumptions.
3. **Debrief with participants** - Share early takeaways and thank them for their candor.
4. **Schedule Target State VSM** - Define the next target conditions using the VSM output.

> _“The goal isn’t just the map—it’s momentum. Use your VSM to drive the next best improvement toward better mission outcomes.”_

#### Step-by-Step Target State VSM Facilitation

1. Present a quick overview of the Current State VSM
2. Highlight the NVA and RNVA steps, major lead time (LT) and process time (PT) differences, low %C&A values
3. Clarify any key questions or assumptions
4. For the key problem steps, a brainstorm improvement process step
5. Encourage “big vision” thinking, no idea is too big at this point
6. Focus on: Eliminating NVA steps entirely, reducing lead time (LT), improving %C&A, streamlining RVNA steps
7. Group ideas around steps the ideas will replace
8. Synthesize based on type of improvement
9. Start with the first step in the value stream map
10. Clearly outline for each new step

    - Process step (value add, required non-value add, or non-value add)
    - Estimate process time (PT) and lead time (LT)
    - Estimate %C&A
    - Write a concise description of the Target State -- include any proposed features or technology
    - Add the current state step(s) being eliminated or changed

11. Calculate total lead time (LT), total process time (PT), and rolled %C&A
12. Calculate the % improved for total lead time (LT), total process time (PT) , and rolled %C&A
13. Focus on the prompt: “Does this Target State get us closer to our goal? What’s the significance of the improvement?”

<br/>

## What Comes After a VSM?

Now that you have a Value Stream Map, it’s time to **act on it**:

### Next Play Recommendations

| Next Play's to Consider | Why It Follows VSM |
|-----------|--------------------|
| **Improvement Kata** | Confirm current and target conditions & prioritize changes to test how you could unblock value |
| **Domain Modeling ([DDD Event Storming](../engineering/DDD-Eventstorm.md), [Boris](https://labspractices.com/practices/boris/), [Swift Method](https://www.youtube.com/watch?v=7-fRtd8LUwA))** | Model the supporting systems and bounded contexts |
| **[Service Blueprint](../design/service-blueprint.md)** | Define user experience & operational architecture |
| **[Impact Mapping](../product/impact-mapping.md)** | Clarify initiative scope by tying improvements to outcomes in prod with measurable user/system behavior changes & mission impact |
| **[Outcome-oriented Roadmap](https://delivery-playbooks.rise8.us/content/practices/outcome-oriented-roadmaps/)** | Communicate and align your team and stakeholders to what gets worked now, next and later to address our value stream current conditions |

---

### Relevant Links & Resources

- **eBook**: [4 Easy Steps to Mastering Chaos with VSM](https://enterprise-software.broadcom.com/valueops-connectall-insights) – Useful to contextualize modern software VSM.
- **Book**: [Value Stream Mapping – Essential for understanding the lean and facilitation discipline behind VSM](https://www.goodreads.com/book/show/17718225-value-stream-mapping).
- **eLearning Courses: [Value Stream Transformation Part 1 of 2](https://tkmgacademy.com/courses/value-stream-transformation-part-1/) [Value Stream Transformation Part 2 of 2](https://tkmgacademy.com/courses/value-stream-transformation-part-2/)**
- **Concept**: *Improvement Kata* – Learn to iterate toward outcomes: [Toyota Kata](https://www.toyotakata.org/)
- **[Digital Operating Model 3: Alignment](https://www.loom.com/share/bab879ee127a4dd6b73fb563b14c79fe)**
- **[RiseU Core Practice of Process Mapping](https://delivery-playbooks.rise8.us/content/practices/process-mapping/)**
- **[Karen Martin’s Value Stream Transformation talk at Prodacity 2025](https://www.rise8.us/videos/value-stream-transformation-mission-accomplished)**
- **[Labs Practices Value Stream Mapping Workshop](https://labspractices.com/practices/value-stream-map/)**
- **[DORA Value Stream Map](https://dora.dev/guides/value-stream-management/)**
- **[Theory of Constraints & Lean Manufacturing](https://www.leanproduction.com/theory-of-constraints/)**


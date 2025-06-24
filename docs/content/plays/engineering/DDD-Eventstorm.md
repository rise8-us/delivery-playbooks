## `DDD Eventstorm`

### What is it? 

* Event Storming serves as a highly collaborative workshop integral to Domain-Driven Design, facilitating the rapid discovery and exploration of a domain's core business processes.  
* It can be employed **strategically** to identify Bounded Contexts and their relationships by mapping out key domain events across an entire system, or **tactically** to flesh out Aggregates, Commands, and deeper business rules within a specific context.  
* It is focused on how the system **wants to behave, not** how it **behaves currently**.

### Why do it? 

* It immerses a software team in the business's operational flow, defining bound contexts and fostering a **Ubiquitous Language**.    
* Empowers software engineers by enabling them to gain a deep understanding of the underlying business logic, resulting in the creation of more accurate, resilient, and valuable software solutions.

### When to do it?

* Strategic  
  * **Starting a New Project or Product:** Before writing any significant code, a strategic Event Storm helps the entire team (business and technical) gain a shared, big-picture understanding of the entire problem space. This ensures you're building the right thing and can anticipate architectural needs.  
  * **Addressing a Growing Monolith or System Complexity:** If an existing system is becoming unmanageable, difficult to change, or has tangled logic, a strategic Event Storm can help identify natural seams and potential Bounded Contexts.  
  * Discover the **Ubiquitous Language** that exists across your various Bounded Contexts.  
* Tactical  
  * **DDD Implementation:** When you're ready to define the aggregates, entities, value objects, domain services, and repositories that will form the backbone of your code within a Bounded Context, the tactical Event Storm provides the granular detail needed.  
  * Perfect a **Ubiquitous Language** within its boundary, right down to the naming of classes and methods in the code.

### Who to Involve?

* **Facilitator** (Mandatory):  
  * Someone impartial who understands Event Storming and can guide the session, keep it on track, and ensure everyone participates. This person should not be a primary domain expert or developer for the domain being mapped, to remain objective.  
  * Why they're critical: To manage the flow, enforce rules, and ensure the desired outcomes are achieved.  
* **Domain Experts** (Absolutely Essential):  
  * These are the people who live and breathe the business process you're mapping. They understand the rules, the nuances, the exceptions, and the current challenges.  
  * Examples: Product Owners, Business Analysts, Department Heads, Subject Matter Experts (SMEs), Customer Service Representatives, Sales Managers, Operations Staff, Legal/Compliance officers.  
  * Why they're critical: They define the "what" and the "why." Without them, you risk building software that doesn't solve real business problems or misunderstands existing processes.  
* **Engineers** (Absolutely Essential):  
  * The engineers who will be building the system.  
  * Examples: Software Engineers, Architects, Technical Leads, Platform Engineers, Cybersecurity Engineers, SREs and CI/CD Engineers.  
  * Why they're critical: They need to understand the domain deeply to translate business needs into code. Their technical questions can also help uncover hidden assumptions or ambiguities in the business process. They also bring feasibility insights.  
* **Product Managers/Owners:** (Recommended)  
  * They bridge the gap between business strategy, customer needs, and technical execution.  
  * Why they're critical: They ensure the discussion stays focused on delivering value and that the identified solutions align with the product roadmap.  
* **UI/UX Designers:** (Recommended)  
  * They bring the customer's interaction and experience perspective.  
  * Why they're critical: They can help identify how users interact with the system, leading to better-defined commands and user-facing events.

### Tools You Might Need

* Whiteboarding tool (figjam, miro) or Post-Its and Sharpies.

### Time You Might Need

* Prioritize the quality of collaboration and outcome over sticking rigidly to a timebox. Be flexible and willing to adjust the schedule according to the group's energy and progress.  
* **Strategic** “Big Picture” Event Storms:  
  * **Duration**: Typically 1 to 3 full days.  
  * **Reasoning**: These sessions aim to map the entire business domain, discover Bounded Contexts, and establish the high-level Ubiquitous Language. This involves a lot of initial exploration, surfacing conflicts, and reaching a shared understanding across a broad area. Trying to rush this often leads to superficial results.  
  * **Format**: Often structured with a half-day or full-day session, followed by a break and then another session to solidify insights.  
* **Tactical** "Process Modeling" / "Design Level"  Event Storms:  
  * **Duration**: Can range from half a day (3-4 hours) to 1.5 days.  
  * **Reasoning**: Once a specific Bounded Context is identified, these sessions delve into the detailed workflow, commands, aggregates, and policies within that context. The scope is narrower, allowing for more focused, intense work.  
  * **Format**: A focused half-day session can be highly productive, especially if the team is already familiar with Event Storming and the context. For more complex contexts, a full day or a day and a half might be needed.

### How to do it

#### Strategic Eventstorm

The primary goal is to discover Bounded Contexts and their high-level interactions across a very broad domain. The scope is the entire business or a large segment of it.

* **Breadth over Depth:** You're rapidly identifying all significant events across the entire domain. Less time is spent on the intricate details of each event's consequences.  
* **Chronological Flow:** The main focus is getting events in the correct relative time order, creating a comprehensive timeline.  
* **Boundary Identification:** The main purpose of this phase is to see where the language and concepts naturally cluster and where they shift, indicating potential Bounded Context boundaries.  
* **Focus on High-Level Commands/Actors:** You identify the major actors (users, external systems) and the primary commands that trigger the core events. The "why" (commands) and "who" (actors) are important for understanding the flow across contexts.  
* **Minimal Detail on Aggregates/Policies:** You might hint at where aggregates could form or where policies exist, but you don't go into detail on their internal structure. Their main purpose here is to help delineate contexts.  
* **Relationships between Contexts:** A crucial strategic step is mapping the relationships between the identified Bounded Contexts (e.g., using different colored lines to show data flow or dependencies).  
* **Outcome and Artifacts:**  
  * A large wall covered with orange events and high-level commands/actors.  
  * Clearly drawn Bounded Context boundaries.  
  * A Context Map showing how Bounded Contexts interact.  
  * A shared, high-level **Ubiquitous Language**.  
  * Identified "Hot Spots" (problem areas) that might warrant their own tactical sessions.

#### Tactical Eventstorm

The primary goal is designing the detailed domain model (Aggregates, Commands, Policies, Entities, Value Objects) within a single, already identified Bounded Context. The scope is much narrower and deeper.

* **Depth over Breadth:** You're focused intensely on all events within the chosen Bounded Context. Every event's cause, consequence, and precise meaning are critical.  
* **Trigger-to-Outcome Chains:** You're very interested in the chain of events: "This event happened \-\> it triggered this command \-\> which caused this effect \-\> leading to this next event."  
* **Invariants and Business Rules:** You're actively looking for rules that govern state changes and validate commands.  
* **Deep Dive on Aggregates:** This is where Aggregates become central. For each event, you identify the Aggregate that emitted the event and the Aggregate that will handle the command that caused the event. You're trying to figure out which data belongs together and needs to be transactionally consistent.  
* **Precise Commands:** Commands (blue sticky notes) are very specific, often mapping directly to methods.  
* **Granular Policies:** Policies (purple sticky notes) are explicitly defined as reactions to events within the context, often triggering new commands.  
* **Read Models / Projections:** You often introduce these (green sticky notes) to show where data is consumed or denormalized for specific views or reporting, which is a tactical implementation concern.  
* **Outcomes and Artifacts:**  
  * A segment of the wall (representing one Bounded Context) dense with orange events, blue commands, yellow actors, pink/yellow aggregates, purple policies, and potentially green read models.  
  * A much more detailed and precise **Ubiquitous Language** for that specific context, ready to be translated into code.  
  * A clear understanding of the Aggregates and their invariants, forming the core of your domain model.  
  * Input for writing user stories, specifications by example, and designing the actual code.

#### Steps

1. **Preparation (Pre-Workshop):**  
   * **Define a Clear Goal:** What specific business problem or large domain are you trying to understand? (e.g., "Understand the entire customer lifecycle," "Map our core product delivery value stream," "Identify Bounded Contexts for a new microservices architecture").  
   * **Invite the Right People:** As discussed, a diverse group including key domain experts, product owners, architects, senior developers, and possibly UX/QA. Aim for 6-12 people for effective collaboration.  
   * **Secure a Large Space:** You'll need a very long wall or a large whiteboard if done physically. The longer, the better, as events are placed chronologically.  
   * **Gather Materials:** Lots of sticky notes (different colors are helpful), thick markers, a timer, and some tape if using paper rolls.  
   * **Explain the Basics (Pre-briefing/Intro):** Briefly introduce Event Storming concepts (events, commands, roles, the "past tense" rule for events, color coding) before the main session to save time.  
2. **Introduction & Kick-off (Workshop Start):**  
   * **Facilitator's Role:** Welcome participants, reiterate the goal, set expectations, explain the rules of engagement (e.g., "no debates, just put it on the wall for now," "past tense verbs for events").  
   * **Define the Starting Point:** Ask the group: "Where does the story begin for the domain we're exploring?" This helps anchor the timeline.  
   * **Define the Horizon:** Identify a clear "end point" or the scope boundary.  
3. **Storming Domain Events (Orange Sticky Notes):**  
   * **The Core Activity:** Instruct everyone to write down every **significant thing that happens in the business domain** as a **past-tense verb** on an orange sticky note.  
   * **No Debate:** Emphasize rapid ideation. If there's a disagreement on wording or whether something is an event, write *both* versions and put them on the wall. Ambiguity is a discovery tool at this stage.  
   * **Timeboxed Rounds:** Run short, focused bursts (e.g., 5-10 minutes) where everyone writes events. Play some LoFi background music. Quickly review and repeat as necessary. It's okay if some events are missed, as you’ll be able to add them in later steps.  
   * **Silence is Golden:** Encourage individual thinking and writing, followed by putting them on the wall. Discourage immediate discussion.  
4. **Laying Out the Timeline:**  
   * **Chronological Order:** As events are written, participants stick them on the wall in roughly chronological order, from left to right.  
   * **Dealing with Parallels:** Events happening at the same time can be placed vertically above each other.  
   * **Finding Gaps & Clusters:** This visual arrangement naturally starts to highlight missing events, concentrations of activity, or major shifts in the process.  
5. **Narrate the Story & Question:**  
   * **Walk the Wall:** The facilitator (or a brave volunteer) walks along the wall, narrating the story of the business domain using only the sticky notes.  
   * **Ask "Why" and "What If":** This narration immediately exposes inconsistencies, missing steps, or areas of confusion. "Why did that happen?" "What happens next?" "What if X failed?"  
   * **Add Missing Events:** As questions arise, new orange sticky notes (events) are added.  
6. **Identify Hot Spots / Bottlenecks (Red Sticky Notes):**  
   * Invite participants to place **red sticky notes** on areas of the timeline where there are:  
     * Confusion or disagreement about the domain.  
     * Known business problems or pain points.  
     * Significant complexity.  
     * Bottlenecks or long wait times.  
   * These hotspots indicate areas that need more attention or might delineate future Bounded Contexts.  
7. **Identify Commands & Actors (Blue Sticky Notes):**  
   * For each event, ask: "What triggered this event?" (a **Command** \- blue sticky) and "Who or what issued that command?" (an **Actor/System** \- yellow sticky).  
   * Place commands to the left of the event they cause, and actors/systems above the command. This builds out the causal chain.  
8. **Identify Policies (Purple Sticky Notes):**  
   * These are the rules or reactions to events. "When \[Event happens\], then \[Policy causes something else to happen\]."  
   * Place them between an event and the command/event it triggers.  
9. **Identify External Systems (Gray Sticky Notes \- Optional):**  
   * If relevant, add notes for external systems (e.g., Payment Gateway, CRM) that interact with your domain.  
10. **Discover Bounded Contexts:**  
    * **Look for Consistency:** Observe clusters of sticky notes (events, commands, actors) where the Ubiquitous Language feels consistent and specific.  
    * **Look for Handoffs/Translations:** Identify where concepts change meaning or where there are significant data transformations. These are often the boundaries.  
    * **Draw Boundaries:** Use long lines or tape (or a different colored long sticky note) to draw rectangles around these consistent clusters. These are your candidate **Bounded Contexts**.  
    * **Name the Contexts:** Collaboratively give each Bounded Context a meaningful, business-oriented name.  
11. **Define Relationships Between Contexts (Context Mapping):**  
    * **Map Interactions:** Draw lines between Bounded Contexts to show how they communicate (e.g., via events, API calls, shared databases).  
    * **Identify Relationship Types:** Briefly discuss the nature of these relationships (e.g., Shared Kernel, Customer/Supplier, Conformist, Anti-Corruption Layer). This is a bridge to strategic DDD patterns.  
12. **Review & Refine:**  
    * **Walk the Contexts:** Review each identified Bounded Context, ensuring its events and commands make sense within its boundary.  
    * **Address Ambiguity:** Discuss any remaining hot spots or ambiguous terms. Decide if terms need to be refined, split, or if new contexts are needed.  
    * **Capture Decisions:** Document key decisions and the agreed-upon Ubiquitous Language for each context.  
13. **Photograph & Digitize** (when done physically)**:**  
    * Take high-resolution photos of the entire wall.  
    * Consider digitizing the map using tools like Miro or Mural for easier sharing and future reference.

#### Stickies

**Domain Event (Orange 🟠):**

* **What it is:** A significant fact about something that happened in the business domain. It's an outcome, a result, or a state change.  
* **Syntax:** Always written in the **past tense** (e.g., "Order Placed," "Payment Processed," "User Registered," "Inventory Updated," "Shipment Dispatched").  
* **Role:** These are the backbone of the Event Storm. They define the narrative of your domain. You start by identifying these.  
* **Placement:** Placed on the main timeline, from left to right in chronological order.  

**Command (Blue 🔵):**  
* **What it is:** An action or request that triggers a Domain Event. It's an intention to make something happen.  
* **Syntax:** Written as a **verb in the imperative mood** (e.g., "Place Order," "Process Payment," "Register User," "Update Inventory," "Dispatch Shipment").  
* **Role:** Explains *why* an event happened. Commands lead to events.  
* **Placement:** Placed immediately to the left of the Domain Event it causes.  

**Actor / User / External System (Yellow 🟡):**  
* **What it is:** The person or external system that initiates a Command.  
* **Syntax:** Noun (e.g., "Customer," "Warehouse Worker," "Payment Gateway," "CRM System," "Scheduler").  
* **Role:** Identifies who or what is performing the action.  
* **Placement:** Placed above the Command they issue.  

**Aggregate (Pink 🌸) :**  
* **What it is:** A cluster of Entities and Value Objects that are treated as a single unit for data changes, ensuring transactional consistency. It has an Aggregate Root that is the only entry point for changes within the aggregate.  
* **Syntax:** Noun, usually singular (e.g., "Order," "Product," "CustomerAccount," "Invoice").  
* **Role:** These are the transactional boundaries. Events originate from Aggregates, and Commands target them. They enforce business rules (invariants).  
* **Placement:** Usually placed above the events and commands they are associated with, often encircling them visually. This is more prominent in tactical Event Storms.  

**Policy / Reaction (Purple 🟣):**  
* **What it is:** A business rule or reaction that triggers a new Command or Event when a specific Domain Event occurs. It represents a side effect or a consequential action.  
* **Syntax:** Often a phrase like "When \[Event\] then \[Command/Action\]" or "If \[Condition\] then \[Action\]." (e.g., "When Order Placed then Notify Warehouse," "If Payment Fails then Refund Customer").  
* **Role:** Shows how events lead to further actions within the system, often automating responses.  
* **Placement:** Placed to the right of the Domain Event it reacts to, and to the left of the Command/Event it triggers.  

**Read Model / View (Green 🟢):**  
* **What it is:** A data projection or a specific view of data optimized for queries or displaying information to a user. It represents a source of information.  
* **Syntax:** Noun (e.g., "Customer Dashboard," "Product Listing Page," "Order History").  
* **Role:** Identifies where information is consumed. It often consumes data from events.  
* **Placement:** Placed above the events that contribute data to it, or above the actors/users who view it. More common in tactical Event Storms.  

**Hot Spot / Problem (Red 🔴):**  
* **What it is:** An area of pain, confusion, disagreement, or a known bottleneck in the current process.  
* **Syntax:** A short description of the problem (e.g., "Manual Handoff," "Frequent Errors," "Conflicting Definitions," "Long Approval Time").  
* **Role:** To highlight areas that need further discussion, clarification, or are candidates for improvement.  
* **Placement:** Placed directly on or near the events/commands/areas where the problem occurs.

### Glossary

**Domain:** The sphere of knowledge, influence, or activity for which the user is building the application. It represents the subject area of the software.

**Subdomain:** A smaller, distinct area within a larger domain, often representing a particular business capability or area of expertise. Can be classified as Core, Supporting, or Generic.

**Bounded Context:** An explicit boundary within a software system where a particular domain model is consistent and its Ubiquitous Language holds a precise, unambiguous meaning. It helps manage complexity by dividing a large domain into smaller, cohesive parts.

**Event Storming:** A collaborative workshop technique used in Domain-Driven Design to rapidly explore and model a business domain by identifying events, commands, actors, and policies. It facilitates shared understanding, discovers Bounded Contexts, and helps define a ubiquitous language.

**Event:** A significant occurrence or fact about something that happened in the business domain, always expressed as a **past tense verb** (e.g., "Order Placed," "Payment Processed").

**Command:** A request or instruction to perform an action within the domain, typically expressed as an **imperative verb** (e.g., "Place Order," "Process Payment").

**Policy:** A business rule or reaction that describes what happens **when** a specific event occurs, often leading to a new command or event (e.g., "When Order Placed then Notify Warehouse").

**Actor:** A person or external system that initiates a command or interacts with the system (e.g., "Customer," "CI Pipeline," "Payment Gateway").

**Entity:** An object defined by its distinct identity, which persists over time and across different representations (e.g., a specific `Customer` with an ID, a unique `Order`).

**Value Object:** An object defined by its attributes rather than a conceptual identity; it measures, quantifies, or describes a thing and is immutable (e.g., an `Address` with street, city, zip, or `Money` with amount and currency).

**Aggregate:** A cluster of associated Entities and Value Objects that are treated as a single unit for data changes, enforcing transactional consistency and business rules through a designated "Aggregate Root" entity.

### Relevant Links

* [Domain-Driven Design Practice](https://delivery-playbooks.rise8.us/content/practices/domain-driven-design/)
* [Figjam Eventstorm Template](https://www.figma.com/board/cweMw6Yq7ldKCz6KEDN6be/Eventstorm-Template?node-id=0-1&p=f&t=k7UtLcx5BhaS0yVF-0)



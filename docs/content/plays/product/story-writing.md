# Story Writing 

![User Story Example](../../../assets/userstory.png)

## What Is It? 

A story is a tool to communicate and track a small piece of work within a balanced product team. All agile development teams leverage stories to represent and manage engineering work in a backlog (see next section for an overview of backlogs). Working off your roadmap, you can break down the listed feature sets into user stories in order to begin work towards the features/epics that you hypothesize will help achieve your stated outcome(s). A good story not only details work to be accomplished with clearly defined success criteria, but it also helps communicate why that work is important which in turn helps the team deliver the best possible solution.
There are three different types of user stories that will commonly populate a product team’s backlog:

**Features:** New functionality intended to add direct value to a user

**Bugs:** Unintended behavior

**Chores:** Everything else (tech debt, spikes, dependency updates, etc)

## What makes a good story?
As we initially mentioned, a story’s primary goal is to function as a communication tool for a balanced team. Sizing and writing successful stories is an iterative process informed by team feedback, so think of every story you write as a placeholder for conversation that will get fine tuned when it is pointed and prioritized during iteration planning. A story should be easy for all disciplines to understand so the team can align on work to be delivered, and you should not be the one to prescribe specific design or engineering implementations.
There are several frameworks for writing stories, but we recommend starting with the INVEST model. Following this method will help you achieve many of the attributes of a successful story.

**Independent:** Aim to have each story be releasable once delivered. Keeping stories independent ensures the application can always be deployed regardless of work completed or not.

**Negotiable:** Be open to making changes to a story based on feedback from your team, both in scope and presentation. 

**Valuable:** Each story should communicate some form of added value to the user or product team, even if it is small and incremental.

**Estimable:** A story should be defined enough so the engineering team can easily discuss implementation. Iterate with the team until you can reach this point. If a team cannot point within 5 minutes then it may mean that the story needs clarification. 

**Small:**  Always push to keep stories small and get help from your team when breaking down big features. Aim for stories that can be completed in 1 day with the biggest ones taking no more than a week. 

**Testable:** A story should have detailed acceptance criteria that will outline the steps you will take to test if the functionality has been added after it has been delivered. This helps engineers write tests and aligns the team on what success looks like to avoid unintended behaviors requiring rework.

## Why Do It? 

A story is a tool to communicate and track a small piece of work within a balanced product team. All agile development teams leverage stories to represent and manage engineering work in a backlog. 

## When To Do It?
User stories are typically written during the early stages of a software development project, specifically during the planning and requirement gathering phase, however, stories are written during the entire life cycle of the project. They serve as a means to capture the features or functionalities desired by users from their perspective.  User stories are used to define the requirements in a way that is easily understandable by both the development team and the stakeholders.

## Who to Involve?
User stories are usually written collaboratively by members of the development team, including product owners, developers, designers, and testers. They focus on the user's needs, goals, or tasks to be accomplished within the software system.

In general a PM is the primary team member accountable for breaking down outcomes into properly scoped stories, communicating the user value of each story, writing the acceptance criteria, and ensuring the formatting is easy to understand. That said, it is not solely your responsibility to take a story from inception to completion. The designer is responsible for outlining the design interactions and styling for the story as well as providing mockups, prototypes, design guides, and/or annotations for the engineers to reference. The engineers contribute execution strategy, architecture patterns, and best practices. Engineers can also be encouraged to write chores since they have a much better understanding of the technical work that needs to be done, and any team member should be empowered to write a bug report if they discover one. These are all team norms that you will work out over time as you iterate.

We recommend involving your team members early and often when scoping out stories to avoid having to go back to the drawing board during an Iteration Planning Meeting (IPM). If you are struggling to break down a large feature set into stories, consider facilitating a story mapping session before your pointing meeting where you get feedback from design and engineering.

## Tools You Might Need

* **Agile Project Management Software:** There are various project management tools specifically designed for Agile methodologies, such as Jira or Github. These platforms often provide features for creating, organizing, and tracking user stories, as well as managing iterations and backlogs.
* **Whiteboards or Sticky Notes:** Physical whiteboards or sticky notes are often used during brainstorming and collaborative sessions to jot down user stories. They offer a tactile and visual way to organize and prioritize ideas.
* **Diagramming Tools:** Diagramming tools like Miro, Figma, Lucidchart or draw.io can be useful for creating visual representations, such as flowcharts or diagrams, to supplement user stories and provide additional clarity.


## How To Do It (Steps)
1. **Identify the User:** Clearly define who the user or persona is that will be interacting with the system. Understanding the user's role, goals, and needs is essential for crafting relevant user stories.

2. **Define the Goal:** Determine what the user wants to achieve or the problem they need to solve. The user story should articulate the desired outcome or benefit from the user's perspective.

3. **Write the User Story:** Use the standard user story format: "As a [type of user], I want [some goal] so that [some reason]." This format helps to focus on the user's needs and the value they expect to derive from the feature. For example:
    * **AS AN** (user persona) Amazon repeat customer
    * **I WANT** (capability) to re-buy something I recently purchased, quickly
    * **SO THAT** (user impact) I don’t waste time looking for & purchasing it

4. **Include Acceptance Criteria:** Specify the conditions that must be met for the user story to be considered complete and satisfying the user's requirements. Acceptance criteria help to clarify expectations and guide development and testing. For example:

    * **GIVEN** (conditions) a user that purchased an item in the last 7 days
    * **WHEN** (actions) they login
    * **THEN** (results) recently purchased items have a ‘buy it again’ option
    * **AND WHEN** (action) selected
    * **THEN** (result) the item is placed in the users cart

5. **Prioritize User Stories:** Arrange user stories in order of priority based on factors such as business value, user impact, dependencies, and technical feasibility. This helps the team focus on delivering the most valuable features first.

6. **Estimate Story Points:** Assign relative estimates, such as story points or t-shirt sizes, to user stories to indicate their complexity and effort required for implementation. This aids in iteration planning and resource allocation.

7. **Refine and Collaborate:** Review user stories with the development team and stakeholders to ensure clarity, completeness, and feasibility. Refine the stories as needed based on feedback and discussions.

8. **Break Down Larger Stories:** If a user story is too large or complex, consider breaking it down into smaller, more manageable stories that can be implemented and delivered incrementally.

9. **Keep Stories Small and Independent:** Aim for user stories that are small enough to be completed within a single iteration and are independent of each other. This promotes agility, flexibility, and easier tracking of progress.

10. **Iterate and Adapt:** User stories are not set in stone and may evolve over time as the project progresses and as the team gains more insights. Continuously review, refine, and adapt user stories based on feedback, changing requirements, and lessons learned.

**Note:** A story may include important information for a specific user. Example if a product requires a specific formula for calculations, the formula  should be included in the ticket and can be added within the acceptance criteria as well. 

## Story examples

### Feature

>**Context (Why)**
>
>AS AN (user persona) Amazon repeat customer
>
>I WANT (capability) to re-buy something I recently purchased, quickly
>
>SO THAT (user impact) I don’t waste time looking for & purchasing it
>
>
>**Acceptance Criteria (What)**
>
>GIVEN (conditions) a user that purchased an item in the last 7 days
>
>WHEN (actions) they login
>
>THEN (results) recently purchased items have a ‘buy it again’ option
>
>AND WHEN (action) selected
>
>THEN (result) the item is placed in the users cart
>
>
>**Design Criteria (How)**
>
> - High Fidelity Design: https://www.somelink.us/design1
> - When, where, and how the ‘buy it again’ option is shown to the user
> - Component format, colors, fonts located in the style guide
> - On hover, buy it again changes color to #AA1212
>   
> **Notes**
>   
> - Discussion: Can we reuse the ‘buyNow’ component?
> - IPM Question: Is it 7 business or calendar days? Answer: Calendar.


### Bug

> **Steps To Reproduce**
> 
> - User purchased an item within last 7 days
> - Navigate to the post-login storefront
> - User views ‘buy again’ component
>
> **Intended Behavior**
> 
> Thumbnails for icons of goods are 640x640 pixels
>
> **Actual Behavior**
> 
> Thumbnails for icons of goods are variable in size
>
> **Notes**
> 
> High Fidelity Design: https://www.somelink.us/design1 


### Chore

> **What**
> 
> - Update java dependency to 17.1+
> - Check scans/pipeline jobs to ensure nothing broke
>
> **Why**
> 
> Version 13 & below is no longer supported, creating a security & reliability risk
>
>**Notes**
> 
> Java 17 documentation can be found here

## Relevant Links
* [How to Write Better User Stories with Gherkin](https://userpilot.com/blog/user-stories-templates/)




# Balancing Coupling In Software Design

## Universal Design Principles for Architecting Modular Software Systems

#### by Vlad Khononov

### Part 1 - Coupling

#### Chapter 1 - Coupling and System Design

- Coupling simply means that something is connected, likewise the strength of coupling is how strongly those 2 things are connected to one another.
- Many times engineers think of coupling as being synonymous with bad design which is not true.  It's impossible to completely decouple components so instead we should strive to find the right level of coupling.
- Related entities that are connected can be as small as springs and gears in a watch that work together to tell time or as vast as galaxies that impact each other with their gravitational pulls.
- There are two main drivers that determine the magnitude of coupling between 2 pieces of software: shared lifecycle and share knowledge.
    1. Shared Lifecycle - This is trivial and often the result of software that exists together in a monolithic system that is built, tested, and deployed together.
    2. Shared Knowledge - This is what knowledge is share across components, the higher the level of shared knowledge across the boundaries the more cascading changes will result.

##### Flow of Knowledge
- Upstream - An upstream component provides a functionality that other components consume.  Its interface exposes the knowledge of its functionality and how to integrate with the component.
- Downstream - A downstream component consumes the upstream component's functionality.  To use the upstream component, the downstream component has to be aware of the knowledge shared through its integration interface.
- Put more simply, downstream components consume upstream components.

##### Systems
> "A system is an interconnected set of elements organized in a way that achieves something." - Thinking in Systems: A Primer by Donella H. Meadows

- There are 3 core elements of a system as detailed by the definition above: components, interconnections, and purpose.
- Often software is a system of interconnected systems in various forms.
- Any system has a set of required components with interactions between them.
- Component design helps to explicitly decide how intergrations work as well as don't work, in a way that's meant to achieve the system's purpose.
- These interactions are what allow the system to achieve it's purpose by orchestrating the work of the components.

> "System design is inherently about boundaries (what's in, what's out, what spans, what moves between) and about tradeoffs.  It re-shapes what is outside, just as it shapes what is inside." - Ruth Malan

- To achieve modular design it's essential to remove accidental coupling while being careful and deliberate about managing essential relationships between components.
- Tolerances are introduced for mechanical engineering to set permissible limits of variation in physical dimensions because it's impossible to create everthing exactly the same every time in manufacturing.

##### Questions to Assess Shared Knowledge Across Coupled Components
- What do components need to know about other components in order to work together?  What will be the impact of a change in that shared knowledge?
- Can you identify components that have to be tested and redeployed only because they share a lifecycle with other, more volatile components?

#### Chapter 2 - Coupling and Complexity: Cynefin

- Complexity reflects the cognitive load that someone experiences in order to understand something.
- Modules that cannot be understood in isolation, but rather only as a puzzle piece that's part of a whole picture are complex.
- Complexity is also somewhat subjective because it is based on the level of understanding a person has on the subject matter.

##### Cynefin

> Cynefin is a Welsh term that embodies the multiple intertwined factors in our environment and our experiences that influence our thoughts, interpretations, and actions--all in ways we can never fully comprehend.

**The 5 Decision Domains**
1. Clear - this is where the effects of an action impacting a system are evident and predictable and follows the sens-categorize-respond approach.
    - Sense: Gather the available information and establish the relevant facts.
    - Categorize: Use the facts to identify the relevant rule or best practice.
    - Respond: Follow the chosen rule or best practice.
    - Example: How we interact with a traffic light on the road.

2. Complicated - this represents "known unknowns", or areas where you recognize insufficient knowledge to make an informed decision.
    - Sense: Gather available information and establish the relevant facts.
    - Analyze: Identify the missing knowledge and consult an expert in the relevant field.
    - Respond: Follow the expert's advice.
    - Example: Car trouble that requires diagnosis and repair from a mechanic.

3. Complex - this is a domain of "unknown unknowns" where you either lack the knowledge as in the Complicated domain but don't have an expert to consult or you don't even know what knowledge is missing and making decisions here requires experimentation since best practices are not predictable.
    - Probe: Conduct a safe experiment to observe the results of different decisions.
    - Sense: Gather the available information, establish relevant facts, and identify patterns.
    - Respond: Follow the course of action according to the experiments' results.
    - Example: Conducting an A/B test on the color of a call-to-action button and analyze click rates.

4. Chaotic - nothing is predictable, you can't consult an expert and it is not possible to perform safe experimentation so you trust your instincts to commit to an action that makes sense in the moment with the goal of transforming the situation from chaotic to complex.
    - Act: Commit any action that makes sense and can potentially help you get out of danger.
    - Sense: Gather the available information on the results of the action.
    - Respond: If you are still in danger, commit another action; plan knowledge-based responses only when you are out of danger.
    - Example:  A natural disaster is impossible to predict the pattern of so acting with your best instincts and then re-evaluating when you're out of danger is best.

5. Disorder - indicates the lack of awareness for which domain you are operating in which requires you to first identify what that domain is.

##### Cynefin in Software Design

**Example 1: Using a Notification System to send SMS messages**
1. Clear: The API method signature receives a phone number type and a specified phone number format.
2. Complicated: The API method signature receives a phone number as a string with no specified number format so you have to ask the author.
3. Complex: The API method signature takes a phone number as a string but we don't have access to the author or source code so we have to experiment to find the right format.
4. Chatoic: The API is behind a load balancer with different versions yielding inconsistent results no matter what format we use.

**Example 2: Changing Database Indexes for a microservice database**
1. Clear: Your team owns the microservice and that microservice is the only application directly interacting with the database.
2. Complicated: Your team and one other team integrates with the database meaning you need to consult them about planned changes.
3. Complex: Other team(s) integrate with the database but you don't know who so you have to test changes and monitor performance in a staging environment.
4. Chaotic: Other team(s) integrate with the database and changes tested in staging causes timeouts in prod so you trust your instincts and roll the change back.


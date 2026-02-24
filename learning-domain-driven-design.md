# Learning Domain-Driven Design

## Aligning Software Architecture and Business Strategy

#### by Vlad Khononov

## Part 1 - Strategic Design
- Domain Driven Design is divided into 2 parts, strategic design and tactical design.
- Strategic design deals with the "what" and "why" which the tactical deals with the "how".

### Chapter 1 - Analyzing Business Domains

- Business Domain - This is what defines a company's main area of activity.  Generally speaking, it's the service the company provides to its clients.
- Subdomain - A fine grained area of business activity.  No one area is enough to make the company successful in it's own right but they are all the building blocks that make up the companies domain.  There are 3 different types of subdomains:
    1. Core subdomain - What differentiates a company from its competitors.  The more complex a core subdomain is the more difficult it will be for competitors to replicate it and narrow their competitive advantage.
    2. Generic subdomain - These are subdomains that all businesses in the space implement.  They may still be complex in nature but do not provide a competitive advantage in the space.
    3. Supporting subdomain - Areas that do not provide a competitive advantage and are required for other domains or subdomains to function and are typically more simple in nature.

- Generic subdomains are typically known unknowns but the knowledge is readily available through other means such as industry-accepted best practices or skilled contractors.
- Could a subdomain be turned into it's own side business?  If so that's likely a core subdomain.
- Is it simpler or cheaper to hack together your own solution to something instead of integrate with another platform?  It's likely a supporting subdomain.

**Solution Strategy**
- Core subdomains should be created in-house, they are a competitive advantage and cannot be bought off of a shelf and should not be farmed out to external teams.
- Generic subdomains, while complex problems of their own, are already solved and it's often less expensive to buy it off the shelf with existing solutions instead of building in-house.
- Supporting subdomains are not complex but there is often not an off the shelf product that can solve them efficiently so building them quickly to enable other systems in-house is the best path forward.

**Identifying Subdomain Boundaries**
- A good starting point can be company departments and other organizational units, these are coarse-grained subdomains though.
- You can get to finer-grain subdomains by looking down a level further, for instance in a call center you may have telephony software, help desk management software, scheduling, etc.
- Ultimately you can continue to drill down to more and more fine subdomains but a good definition to stop at is "subdomains as a set of coherent use cases", meaning the data and actors are tightly bound to the use cases.

**Domain Experts** 
These people are subject matter experts that know all of the business intricacies that need to be modeled and implemented in code.

### Chapter 2 - Discovering Domain Knowledge
> "It's developers' (mis)understanding, no domain experts' knowledge, that gets released in production." -Alberto Brandolini

- Business problems are not just riddles or math equations to solve, they are workflow optimization, process streamlining, labor minimizing, and many more, tools that help the business in it's goal to solve customer problems.

**Mental Model** - The domain experts' way of thinking about a problem.

- Knowledge discovery is the process of understanding the business problem through the perspective of the domain experts and learning to communicate with shared language that they understand.

**Analysis Model** - An engineer-friendly description of the domain knowledge translated into system requirements to build rather than an understanding of the business domain behind it.

- Communication is essential between everyone to ensure that an accurate mental model of the business domain is established so the product team can create and deliver a solution that effectively solves the business problem presented to them.

**Ubiquitous Language** - A cultivated singular language used for describing the business domain instead of continuously translating it based on the step in the process it is discussed.  It must be based on the language of the business and include no technical jargon.

**Ambiguous Terms** - A term cannot have multiple meanings (i.e. policy for regulatory rule or insurance contract) so instead of using "policy" in domain language you would create singular meaning with the separate terms "regulatory rule" and "insurance contract".

**Synonymous Terms** - You cannot use terms interchangeably (i.e. user, visitor, administrator, account) because while they are all users each one of them will have specific roles and use cases within the domain so instead you would want to use the more specific terms.

#### Model of the Business Domain
> "A model is a simplified representation of a thing or phenomenon that intentionally emphasizes certain aspects while ignoring others.  Abstraction with a specific use in mind." - Rebecca Wirfs-Brock

- All models have a purpose, and an effective model contains only the details needed to fulfill its purpose.
- Modeling a business domain is based on a domain experts mental model of how the business works to implement its function and is not meant to capture every possible detail of a domain.
- Creating a ubiquitous language is a continuous effort that should be validated everyday in communication around the work and evolved when deeper insights reveal error or nuance that differs.
- Tools can be used to help enforce the ubiquitous language such as a glossary of domain terms, gherkin tests to manage tests for business use cases, and static code analysis tools to verify the code is correctly using the ubiquitous language.

### Chapter 3 - Managing Domain Complexity
- Models can be inconsistent when terminology is repeated in different sub domains (i.e a sales lead and a marketing lead can mean different things)
- Previous approaches would either:
    1. Create a model that is useable in both scenarios which leads to overly complex ERDs and a model that's over engineered for one domain and under engineered for another.
    2. Add a subdomain prefix, such as "marketing lead" or "sales lead", which creates a divide in the written ubiquitous language and the spoken language since conversationally people do not typically use such prefixes.

**Bounded Context** - A smaller portion of the domain in which the ubiquitous language is broken down into smaller languages based on a domain experts mental model of part of the domain.
- A language's terminology, principles, and business rules are only consistent inside it's bounded context.
- Ubiquitous does not mean universal, the language is ubiquitous within the boundaries of the the explicit context of it's applicability.
- Defining a bounded context is a strategic design decision and may even be based on non-functional requirements (i.e. differences in scaling or delivery).
- It does not matter if a bounded context is large or small, it should be aligned with business and organizational needs.
- Bounded contexts and subdomains are different in that subdomains are discovered based on the business strategy and organization and bounded contexts are designed to address project context and constraints.

> "Architectural design is system design.  System design is contextual design--it is inherently about boundaries (what's in, what's out, what spans, what moves between), and about trade-offs.  It reshapes what is outside, just as it shapes what is inside." - Ruth Malan

**Physical Boundaries** - A bounded context should be an individual project/service that is implemented and versioned independently on the technology stack that best suits its needs.  There can be subdomains within a bounded context that would constitute logical boundaries.

**Ownership Boundaries** - No two teams should own or work on the same bounded context.  A bounded context should only be owned by one team, but any team can own multiple bounded contexts.

### Chapter 4 - Integrating Bounded Contexts
There are three types of groups when considering the integration between teams and their bounded contexts: cooperation, customer-supplier, and separate ways.

#### Cooperation
This is typically the pattern that is used for teams with well established communication, or could even be between 2 bounded contexts within the same team.  The success of one is dependent on the success of the other.
- Changes between the bounded contexts is communicated in an ad hoc manner.  The communication is bidirectional and both sides of the conversation are involved in working through issues and regularly communicate.
- There can be instances where there is a shared model between domains or subdomains, this must be consistent for all bounded contexts.  One change in the shared model affects all bounded contexts that consume it (i.e. permissions models)
- Any shared models should be limited to only expose parts that are used by both bounded contexts, such as integration contracts and data models that are used across boundaries.
- Since this introduces a strong dependency between the involved bounded contexts it should only be leveraged when the cost of duplication is higher than the cost of coordination.
- This pattern contradicts the idea of a single team owning a bounded context and is a pragmatic compromise that should be justified deliberately.

#### Customer-Supplier
In this group of collaborations there is a customer (downstream) and a supplier (upstream) where the supplier provides a service to the customer via some kind of contract and they can generally succeed independently.
- There are three patterns that address the inherent power differences in this group: conformist, anti-corruption layer, and open-host service patterns.
- Conformist is when the supplier has no real motivation to react to its clients needs and the downstream team finds that contract acceptable for integration despite having no say in the contract.
- Anti-corruption layer would be implemented when similarly the balance of the power is with the supplier, however, there are concerns with the contract and the downstream team needs to protect their bounded context from things like frequently changing contracts, or legacy systems that would introduce bad data patterns to your domain.
- Open-host service is when the supplier is highly incentivized to protect the downstream consumers so they create a "published language" that separates the evolution of the integration contract from the evolution of the product domain.  The supplier's goal is not to conform to a ubiquitous language, but to provide a protocol convenient to the customers.

#### Separate Ways
Lastly, there are times when collaborating may not be an option at all, whether thy are unwilling or unable.
- Communication issues can sometimes mean that duplicate functionality is more cost effective in multiple bounded contexts.
- Generic subdomains, such as logging, could be duplicated for each bounded context and may in fact be more cost-effective than forcing all bounded contexts to integrate with and conform to one solution.
- Model differences that are so significant that implementing an anti-corruption layer to create a conformist relationship is more expensive than duplicating functionality.

#### Context Map
This is a visualization that represents a systems bounded contexts and the integrations between them.  I provides visibility into _high level design_, _communication patterns_, and _organizational issues_.

## Part 2 - Tactical Design

### Chapter 5 - Implementing Simple Business Logic
- If technology doesn't solve a business problem then it's just an expensive technology demo.

#### Transaction Script
> "Organizes business logic by procedures where each procedure handles a single request from the presentation." - Martin Fowler

- Each procedure should be transactional, failing at even the worst possible moment should rollback any completed changes or execute compensating actions to ensure a consistent state.
- There are 3 common ways that errors are generated due to improperly implementing the transaction script pattern:
1. Lack of transactional behavior (i.e. updating multiple records without an overarching transaction)
2. Not accurately handling distributed transactions across multiple systems or storage mechanisms.
3. When implicit distributed transactions allow for multiple executions for the same call to create inconsistent state.
- This patterns is well suited for straight forward problem domains where business logic resembles procedural operations like ETL.

#### Active Record
> "An object that wraps a row in a database table or view, encapsulates the database access, and adds domain logic on that data." - Martin Fowler

- Similar to the transaction script pattern, but the business logic may operate on more complex data structures.
- Instead of directly accessing the database, the in memory object maps to the database entities and the operation must complete or fail as an atomic object.
- The distinctive feature for active record objects is the separation of data structures and business logic.
- The active record pattern is essentially a transaction script that optimizes database access, only supporting simple business logic like CRUD operations and input validation.
- This pattern is also known as an anemic domain model antipattern.
- At the end of the day it's important to be pragmatic, at certain levels of scale it's possible that data consistency guarantees are able to be relaxed.

### Chapter 6 - Tackling Complex Business Logic
#### Domain Model Pattern
- Meant for complex business logic that is implemented with complicated state transitions, business rules, and invariants (rules that have to be protected at all times), instead of CRUD interfaces.

#### Implementation 
- A domain model is an object model of the domain that incorporates both behavior and data.
- Complexity should be reduced by using _plain old objects_ that implement business logic without relying on or directly incorporating any infrastructural components or frameworks.
- Ubiquitous language is driven by the business logic and allows the code to "speak" the ubiquitous language and follow the domain expert's model.

#### Building Blocks
- Value object - an object that can be identified by the composition of its values.
    - Ubiquitous language - using value objects you can encapsulate the domain model using the ubiquitous language to encapsulate all aspects of that language (e.g. think of a Height object that instead of being an int allows for imperial and metric measurements, display string formatting, unit conversion, etc.)
    - Implementation - value objects are implemented as immutable objects since the changing of any property results in a different value (e.g. color object MixWith method that mixes two colors and returns a newly instantiated object)
- Entities - the opposite of a value object, it explicitly requires an identification field to distinguish between different instances of the entity (e.g. a Person object with a Name value object would need an identifier because many people share the same name).  They are also not immutable like value objects.
- Aggregates - this is an entity that requires an explicit identification field, is mutable, and must protect the consistency of its data.
    - Consistency enforcement - the boundary of the aggregate is where this enforcement takes place and the logic is meant to ensure that any incoming modifications do not create state that is contradictory to business rules.

> NOTE: All external processes or objects can only read the aggregate's state, and state can only be updated by executing corresponding methods of the aggregate's public interface (often referred to as commands).

> NOTE: The database used for storing aggregates must support concurrency management which, in its simplest form would hold a version field that would be incremented after each update.

    - Transaction boundary - since an aggregate contains all business logic for mutations, it acts as a transactional boundary as well and all entity changes for an aggregate state mutation should succeed or fail as a single atomic operation.  No operation can assume a multi-aggregate transaction.
    - Hierarchy of entities - an aggregate is made of up a group of entities that are all within a transactional bound, which means that these entities should only be updated atomically and in accordance with business logic that is part of the aggregate.
    - Referencing other aggregates - consistency of data is a useful guiding principle, only information that is required to be strongly consistent should be considered part of the aggregate and anything that can be eventually consistent should live outside of this boundary.
    - Aggregate root - since an aggregate represents a hierarchy of entities and they can only be modified by executing a command, the public interface of these commands lives at the aggregate root (e.g. updating a Message on a Ticket, the Ticket is the root)
    - Domain events - a message describing a specific event that has happened in the domain that any part of the system can consume and execute any business logic necessary in response.
    - Ubiquitous language - aggregates should use the same terminology for their names, data members, actions, and domain events as the ubiquitous language so developers and domain experts are speaking the same language as the code.
- Domain services - a stateless object that implements business logic that can often call to various components of the system to perform some calculation or analysis.  
    - The goal is to make it easy to coordinate the work of multiple aggregates.
    - This is not a loophole around the transactional limitation, it's a way of implementing business logic that requires the _reading_ of data of multiple aggregates to perform a calculation.
    - It is also not a microservice, just a stateless object used to host business logic.

### Chapter 7 - Modeling the Dimension of Time
> "Show me your flowchart and conceal your tables, and I shall continue to be mystified.  Show me your tables, and I won't usually need your flowchart; it'll be obvious." -Fred Brooks

#### Event Sourcing
Using the domain model, but adding the dimension of time to track the events that happen to change a domain model so we can see the entire journey of how the model changed from start to finish or any point in between.

- Search - In order to search you would need to use projection to get the current state of whatever the search term is since we would not want mismatches based on historical versions of the data that are no longer applicable.
- Analysis - You can also use projection to specific data points to allow analysis for business needs such as finding converted leads and how many follow ups it took to convert them.
- Source of Truth - All of the events that make up the changes to an object's state should be persisted to a database and should be the systems source of truth.  This should be the only strongly consistent storage, known as the _event store_.
- Event Store - Where all events are persisted.  It should not allow the modification or deletion of events and it append only.  At a minimum the system should allow the ability to fetch all events belonging to a specific entity, and to append an event.  The expected version should be part of the append method and if the expected version does not match you should receive a concurrency exception.

#### Event-Sourced Domain Model
Instead of a maintained state of the aggregate that can emit domain events to enact changes, the event-sourced domain model uses domain events exclusively to model the lifecycle of aggregates following this script:
1. Load the aggregate's domain events
2. Reconstitute a state representation - project the events int a state representation that can be used to make business decisions
3. Execute the aggregate's command to execute the business logic, and consequently, produce new domain events
4. Commit the new domain events to the event store

While this approach adds more complexity there are some advantages that come with it.
- Time Traveling - Since you have a record of every event you can easily use this to analyze system behavior or perform debugging using this data.
- Deep Insights - Having all of the events allows you to gain more insights to the system by adding more projections since you can always enhance the way the events are looked at in aggregate.
- Audit Log - This approach provides a strongly consistent audit log of every event out of the box.
- Advanced Optimistic Concurrency Management - Instead of race conditions that might overwrite entity models out of order you can use version tracking to make sure your event is not persisted in a bad state.

Along with the advantages there are naturally some disadvantages that come with this approach as well.
- Learning Curve - Since this is a departure from traditional data management the team will likely require some training and a bit of time to adapt to this new way of thinking.
- Evolving The Model - The strict definition of event sourcing is that events are immutable so changing the event's schema is not as simple as updating a table schema.
- Architectural Complexity - This approach introduces numerous "moving parts" which makes overall design more complicated.

#### Frequently Asked Questions
> Q: Won't reconstituting an aggregate from an event cause performance issues as events are added?
> A: While it's important to check performance benchmarks you will not see noticeable hits to performance until you reach over 10,000 events for an aggregate.  If your aggregate is expected to have that many or more you can implement the snapshot pattern where a process constantly creates cached versions of aggregates and then when they are retrieved you can load the cached version then just retrieve the events that have occurred since that cached version was created.

> Q: With how much data this pattern creates can it scale?
> A: It is easy to scale because all aggregate operations are done in the context of a single aggregate.  You can also shard the event store by aggregate IDs, keeping all events of a particular aggregate in a single shard.

> Q: Since this is an append only approach what do you do when you need to delete data physically due to something like GDPR?
> A: Use a forgettable payload pattern where sensitive data is stored encrypted and the key should be stored in an external key store.  Deleting the key from the external store preserves the event while making the sensitive data unreadable.

> Q: Why can't we just write audit logs to a text file instead?
> A: This is error prone since you're writing to two separate storage mechanisms.

> Q: Why not work with a state-based model, but append event logs to a table in the same transaction?
> A: This could ensure that the data between log and state tables are consistent, but it is error prone and when the state-based representation becomes the source of truth the audit logs tend to degrade.

> Q: Why not work with a state-based model that uses database triggers to take record snapshots?
> A: While this addresses the disconnected risk of the previous question, it only contains a snapshot of what changed and loses the business reasons behind the state change.

### Chapter 8 - Architectural Patterns
There are 3 predominant architectural patterns that are explored in this chapter as well as their use cases: layered architecture, ports & adapters, and CQRS.

#### Layered Architecture
- In its classic for it consists of 3 layers, the presentation layer (PL), the business logic layer (BLL), and the data access layer (DAL).
- The presentation layer are a means for the system to receive requests from the external environment wether it be through a UI, CLI, API, event subscripts or message topics.
- The business logic layer encapsulates the implementation of the business rules and is considered the heart of software.
- The data access layer stores all of the persistence logic, which used to strictly be a relational database but in today's technology could be a much broader array of persistence mechanisms.
- The layers are integrated in a top-down communication model where they can only have a dependency on the layer below them: PL->BLL->DAL
- A common extension of this pattern is to add a service layer which acts as an intermediary between the PL and the BLL.
- This pattern is a good fit when the system has business logic implemented using the transaction script of active record pattern.

#### Ports & Adapters
- This architecture addresses some of the shortcomings of the layered architecture and is better fit for implementing business logic that has a higher degree of complexity.
- An infrastructure layer (IL) is a combined representation of the external components of the PL and DAL.
- The dependency inversion principle (DIP) states that high-level modules, which implement business logic, should not depend on low-level modules (this is exactly what layered architecture does).
- To implement the DIP in ports and adapters you revers the nature of the relationship between the BL and the new infrastructure layer, then add the application layer (AL) as the facade for the system's public interface between them: IL -> AL -> BL
- The core goal of this pattern is to decouple the system's business logic from its infrastructural components.
- This architecture is also known as hexagonal architecture, onion architecture, and clean architecture.

#### Command-Query Responsibility Segregation (CQRS)
- This architecture leverages the same organizational principles for business logic and infrastructure as the ports & adapters but manages data differently, using multiple persistent models.
- The polyglot persistence model allows you to store information in multiple database to satiate different data requirements similar to the difference of projected models discussed in chapter 7.
- As the name suggests there is a command execution model and read models.

> **Command Execution Model** - A single model for executing operations that modify the system's state, also known as system commands.  This model is used to implement the business logic, validate rules, and enforce variants.

> **Read Models (Projections)** - A pre-cached model that is used to represent the system's data.  It can be stored in any number of persistence tools and when properly implemented can be wiped out and recreated from scratch.  This enables extending of the system to support additional projections in the future for models that were not previously foreseen.

- A common misconception is that executing a command does not necessarily return any data.  It can, and should, return data because error states need to be handled and projections will be eventually consistent, which means in the immediate term we need accurate data.
- CQRS follows the tenants of using the best tool for the job since you can use different storage mechanisms to best suite the purpose of the projections.

### Chapter 9 - Communication Patterns

#### Model Translation
- Anti-Corruption Layer (ACL) - When a downstream system must translate an upstream systems bounded context model into a usable format for its bounded context.
- Open-Host Service (OHS) - When an upstream bounded context protects its consumers from changes to its implementation by using an integration specific published language.
- The model's translation logic cane be stateless (on the fly) as incoming (OHS) or outgoing (ACL) requests are issued or stateful (more complicated translation logic that requires a database).

#### Integrating Aggregates
- One common mistake is to publish messages as part of an aggregate which risks the event being processed by down stream systems, before the commit of that data state to storage.
- Similarly, moving the message publishing logic to the application layer could fail if the event is processed but the publish fails for some reason resulting in an altered state with a missing message.
- The fix for both of these concerns is the Outbox Pattern using the following algorithm:
    1. Both the updated aggregate's state and the new domain events are committed in the same atomic transaction.
    2. A message relay fetches newly committed domain events from the database.
    3. The relay publishes the domain events to the message bus.
    4. Upon successful publishing, the relay either marks the events as published in the database or deletes them completely.

**Saga** - These are long-running processes (not necessarily in time but in transactions) that span multiple bounded contexts.  The transactions can be handled by aggregates or any component emitting and responding to domain events and commands.  If any event fails the saga is in charge of issuing any necessary compensating actions to ensure system consistency.

**Process Manager** - A process manager follows a very similar structure as a saga but has a centralized process that maintains the state of the sequence and determines the next processing steps.

### Chapter 11 - Evolving Design Decisions
- Domains and subdomains can change their types over time as the business domain evolves and changes which will affect how we treat those domains, here some some common examples:
    1. Core-to-generic - Something that previously gave a company a competitive edge becomes obsolete because competitors can now buy a product that negates that competitive edge.
    2. Generic-to-core - When a company finds an innovative way to gain a competitive advantage in a subdomain that is considered generic by other companies.
    3. Supporting-to-generic - A simple subdomain that is built in house to enable another part of the business is rendered obsolete because a third party tool can be purchased and implemented to standardize a process.
    4. Supporting-to-core - When a simple domain that starts out as primarily CRUD and/or ETL functions but evolves over time to provide a competitive edge by enhancing profitability or efficiency.
    5. Core-to-supporting - If a subdomain is no longer profitable and extraneous complexity gets cut down, leaving behind primarily functionality to enable other subdomains.
    6. Generic-to-supporting - The integration costs to a commercial platform may be too high and in that case perhaps a simple in house solution can replace that platform which would create a supporting subdomain.

#### Strategic Design Concerns
- A change in a subdomain's type directly impacts the bounded context of that subdomain as well as the strategic design decisions.
- If a generic subdomain morphs into a core subdomain it's no longer acceptable to have teams duplicating that functionality.
- Supporting subdomains might be good candidates for outsourcing or ramp up projects for new employees to get their feet wet.

#### Tactical Design Concerns
> "The main indicator of a change in a subdomain's type is the inability of the existing technical design to support current business needs."

- The addition of complex rules and business logic increases the complexity of the code base and creates additional pain for new features.  This "pain" can be a good signal to reassess the domain decisions.
- Needing to change your design is not a bad thing, we design the best we can for where the business is in the moment and evolve with it as the business grows and changes.

**Migration Between Design Implementations**
- Transaction Script -> Active Record - The primary concern here is encapsulating the mapping of complex data structures in active record objects.
- Active Record -> Domain Model - Look for data that can be modeled as immutable objects and related business logic that can be part of a value object.  Identify transactional boundaries.  Then make sure all setters are private to enforce that modifications only happen inside the active record.  Create `Aggregates` for hierarchies that need to ensure strong consistency and make sure external `Aggregates` are only reference by their IDs.
- Domain Model -> Event-Sourced Domain Model - Instead of modifying the data directly, model the `Events` that represent the lifecycle.  Determine if you want to generate past transitions based on current data state or create a migration event to indicate the beginning of the event timeline.

- Organizational changes can also impact bounded contexts as teams grow and have to split into smaller groups or are relocated regionally or reorganized.

#### Domain Knowledge
- It's important to design the bounded context boundaries based on the level of domain knowledge, the more unclear an area is the more broadly you should define a bounded context.
- As domain knowledge becomes more clear you can decompose large bounded contexts into smaller and more narrowly focused bounded contexts.
- Domain knowledge can be discovered and used to evolve the design and make it more resilient.

#### Growth
- Growth is a sign that the system is healthy, successful, and providing value to the users.

> "A big ball of mud is a haphazardly structured, sprawling, sloppy, duct-tape-and-baling-wire, spaghetti-code jungle.  These systems show unmistakable signs of unregulated growth, and repeated expedient repair.  - Brian Foote and Joseph Yoder

- Big balls of mud are the result of unregulated growth when systems are extended without re-evaluating design decisions.
- The best way to deal with complexity that arises from growth is to identify and eliminate accidental complexity caused by outdated design decisions.

### Chapter 12 - EventStorming

> "EventStorming is a low-tech activity for a group of people to brainstorm and rapidly model a business process."

- An EventStorming session needs a defined _scope_ which is a business process for the group to explore.
- Using sticky notes, develop a timeline with steps for the model and enhance it with additional concepts such as actors, commands, external systems, and others.
- The group should be made up of anyone related to the business domain that can provide domain knowledge contributions to the process, but generally this process can get challenging in groups larger than 10.

#### What's Needed For Event Storming
- Modeling Space -  A large empty wall or whiteboard that can be drawn on.
- Sticky Notes - Lots of them with varying colors to represent the different elements of the domain.
- Markers - Used to write on the sticky notes.
- Snacks - Sessions are typically 2 to 4 hours so have food to keep the energy up.
- Room - Spacious room that doesn't have anything dividing the space so it's easy to move around.

#### The EventStorming Process
1. Unstructured Exploration - Using orange sticky notes, everyone writes down domain events in the past tense and puts them on the _modeling space_ until the rate of new events being added slows dramatically.
2. Timelines - Starting with the happy path scenarios and then moving on to the more complex ones, organize the domain events into a timeline based on what order the events occur in and draw arrows to connect them in order.
3. Pain Points - Using rotated (diamond) pink sticky notes, mark any bottlenecks, manual steps, etc. that require attention.  
4. Pivotal Events - Identify events that indicate a change in context or phase and draw a vertical line above and below those events.
5. Commands - Using light blue sticky notes, write commands in the imperative format before the events they produce and annotate the actor using a yellow sticky note attached to it.
6. Policies - Using purple sticky notes indicate any events that trigger an _automation policy_ (or command with no specific actor) with details on what triggers them and arrows connecting the events ans commands.
7. Read Models - Using green sticky notes indicate the views of data that an actor uses to make a decision to execute a command (i.e. a screen, report, notification, etc.)
8. External Systems - Using pink sticky notes indicate any system that is not part of the domain being explored but might execute a command (input) or be notified about events (output).
9. Aggregates - Using large yellow sticky notes start organizing related concepts in aggregates and define commands on the left and events on the right.
10. Bounded Contexts - Look for aggregates that are related by functionality or policies and determine bounded context boundaries.

#### When To Use EventStorming
- Build a ubiquitous language
- Model the business process
- Explore new business requirements
- Recover domain knowledge
- Explore ways to improve and existing business process
- Onboard new team members
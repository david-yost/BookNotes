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
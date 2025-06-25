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

#### Chapter 3 - Coupling and Complexity: Interactions

##### Complexity and System Design

When dealing with complexity within systems there are primarily two ways of defining the way the components of a system interact with each other, linear and complex.

Linear Interactions - Clear and predictable with obvious dependencies between components.  The cause-and-effect relationship between components is clear and changes introduced are clear on how the changes will impact components around it.

Complex Interactions - Neither clear nor predictable.  Interactions either create unintended effects or the intended effects are created in unexpected ways.
    1. Intended Effects in Unexpected Ways - A system producing intended effects in unexpected ways that no one understands.  Can happen for many reasons including loss of all personnel with knowledge of the system, too much accidental complexity, or inheriting a code base with an unfamiliar technology stack.
    2. Unintended Results - These are accidents and system failures, and can still be present in complex interactions that achieve their goals.  Usually this is a symptom of implicit knowledge, whether that an assumption about the environment or a poorly constructed code base.

##### Complexity and System Size

The number of components does not determine the complexity of a system.  You can have systems with thousands of components that are less complex than a system with only a handful, the key difference is whether the interactions between those components are linear or complex.

##### Hierarchical Complexity

System complexity is multidimensional and interactions, whether complex or linear, can take place between components of a system or within components themselves.

**Global Complexity** is the complexity of interactions between the system's components.
**Local Complexity** is the complexity of a single component--the complexity of interactions happening inside it.

##### Degrees of Freedom

> **Degrees of freedom** is used in mechanics, thermodynamics, and other fields to describe the movement and behavior of physical systems.  It refers to the number of independent variables that can take on different values without being constrained by other variables.

- Degrees of freedom can be limited somewhat by adding constraints to the variables.  (i.e. triangle class that verifies the sum of any 2 sides is greater than the third)
- "Order in a system, and its future outcomes, are predictable as lon gas the system has constraints and the constraints can be sustained." - Snowden 2020
- The fewer constraints that you can work with the less certainty you have about cause-and-effect relationships which means greater complexity.

#### Chapter 4 - Coupling and Modularity

> "At its core, modularity refers to systems composed of self-contained units called modules."

**Fundamental properties to describe a module**
1. Function - The modules goal.  It's exposed to the consumers of the module through its public interface.  The interface has to reflect the tasks that can be achieved by the module, how the module can be integrated, and its interactions with other modules.
2. Logic - How the module's function is implemented; that is, the implementation details of the module.  Unlike function, which is explicitly exposed to consumers, a module's logic should be hidden from other modules.
3. Context - The environment in which the module should be used.  This includes both explicit requirements and implicit assumptions the design makes on the module's usage scenarios and environment.

##### Software Modules
A Module is any collection of executable program statements meeting all of the following criteria:
1. The statements implement self-contained functionality.
2. The functionality can be called from any other module.
3. The implementation has the potential to be individually compiled.

##### Modules as Abstractions
- Abstractions can be used to craft software boundaries
- The goal of an abstraction is to represent multiple things equally well (i.e. car doesn't specify make, model, or color)
- For the abstraction to work well it must eliminate details that are relevant to concrete cases but are not shared by all

##### Modularity, Complexity, and Coupling
Modularity controls complexity of a system in two ways:
1. Eliminating accidental complexity; in other words, avoiding complexity driven by the poor design of a system
2. Managing the system's essential complexity.  The essential complexity is an inherent part of the system's business domain and, thus, cannot be eliminated.  On the other hand, modular design contains its effect by encapsulating the complex parts in proper modules, preventing its complexity from "spilling" across the system.

The three properties of a module define three types of knowledge reflected by the design of a module:
1. Function: the explicitly exposed knowledge
2. Logic: knowledge that is hidden within the module
3. Context: knowledge the module has about its environment

> Effective module design maximizes the knowledge it encapsulates, while sharing only the minimum that is required for other components to work with the module.

### Part 2 - Dimensions

#### Chapter 5 - Structured Design's Module Coupling

**Module Coupling** - A model proposed by structured design that describes six levels of interconnectedness: content, common, external, control, stamp, and data coupling.
1. Content Coupling - Also known as pathological coupling, is when a downstream module references an upstream module's content directly instead of through the publicly defined interface.
2. Common Coupling - This can occur when two modules are using a globally shared data structure.  Some common effects include the following:
    - Sharing more information between modules than is necessary.
    - Integration contracts between module is implicit, making changes more difficult.
    - Data flow between modules is difficult to track.
    - Duplicate business logic, like validation, between modules.
    - The potential for race conditions.
3. External Coupling - Just like _Common Coupling_ the modules are communicating through shared data, however, integrated modules aren't exposing all of their data and instead only share data needed for integration.  The effects of _External Coupling_ are pretty much identical to _Common Coupling_ because it's the same principal with a smaller dataset.
4. Control Coupling - When one module controls the internal execution of another module, usually by passing in flags, commands, or options.  Some effects of _Control Coupling_ are:
    - Inability to control execution flow.
    - Module function AND logic is exposed through its public interface.
5. Stamp Coupling - When two modules communicate by passing data structures that are revealing some of their implementation details.
    - The primary effect is overexposure of data to integrated modules,  making it difficult to know what you can change safely.
    - The biggest difference from _Common Coupling_ is that no business logic is shared across boundaries.
    - The biggest difference from _Control Coupling_ is that only data structures are shared in _Stamp Coupling_ and no behavioral knowledge is shared.
6. Data Coupling - The lowest level of coupling where no business logic is shared and only the minimum amount of data needed for integration is shared across modules.

#### Chapter 6 - Connascence

Connascence is a Latin word that means "having been born together" and in terms of software design mean that the lifecycles of two modules are intertwined.

**Types of Connascence**
1. Static connascence - describes interconnectedness between the module at the source code level; that is, its compile-time relationships.
2. Dynamic connascence - describes the runtime relationships between the components, or how functionalities implemented in different modules affect each other during execution.

##### Static Connascence
- Connascence of name - the weakest level of interconnectedness on the connascence scale that implies to reference the same things, connected modules must agree on its name.
- Connascence of type - when two modules must agree on the use of a specific type.  It is a slightly higher level of connascence than that of name.
- Connascence of meaning - two modules attribute special mean to specific values, and these "magic values" are passed across boundaries.
- Connascence of algorithm - two modules must agree on the usage of a particular algorithm to understand the values passed across their interfaces.  A common use case of this is when sending/receiving encrypted data.
- Connascence of position - multiple modules need to agree on a specific order of elements.  For instance arguments in an array.

##### Dynamic Connascence
- Connascence of execution - multiple modules exhibit this when their execution must follow a specific sequence.
- Connascence of timing - multiple modules exhibit this when their execution must follow a specific sequence and with a specific time interval between them.
- Connascence of value - values that have to change simultaneously, such as an atomic transaction, or that otherwise place the system in an incorrect state, are connascent by value.
- Connascence of identity - when two objects need to reference the exact same instance of a third object to operate correctly.

#### Chapter 7 - Integration Strength

##### Strength of Coupling
**There are 2 scales of interconnectedness that reflect two key properties of inter-module interactions:**
1. Interface type: Modules and communicate through private or public interfaces, private interfaces require more knowledge sharing and thus tighter coupling typically.
2. Interface complexity: The more knowledge that is shared between modules the greater the chances that their interactions are more complex.

> One of the blind spots of the coupling model is logic that is duplicated in otherwise disconnected modules.  For instance, if free shipping gets applied for orders over $1000 and that logic exists independently in 2 different modules but those modules do not directly interact they must still change together because of this shared knowledge.

##### Integration Strength
This model aims to achieve the following goals:
- Practicality: Integration strength should be easy to grasp and to apply in day-to-day work.
- Versatility: Enable evaluating the strength of coupling for all kinds of modules, from individual lines of code to services within a distributed system.
- Completeness: Address the shortcomings and blind spots of module coupling and connascence.

The 4 fundamental levels of integration strength:
1. Contract coupling
2. Model coupling
3. Functional coupling
4. Intrusive coupling

The different fundamental levels of integration will be discussed below with reference to the book's working example of 2 services accessing the same database.

##### Intrusive Coupling
- Instead of communicating through public interfaces, the modules downstream rely on implementation details of the upstream module.
- Reflection can often be used in intrusive coupling but is not in and of itself definitive of intrusive coupling (see ORM example)
- Functional example: In a micro-service infrastructure, if the database belongs to Service A and was not meant to be an integration interface, but Service B is also accessing this database that would mean Service B is dependent on Service A's implementation details.
- Some effects of intrusive coupling are:
    1. It's very fragile because any change to the upstream module could break the integration with downstream components.
    2. This is the most implicit integration interface and upstream modules are often not even aware of it.
    3. It breaks encapsulation by not hiding as much knowledge as possible behind the boundaries of the module.

##### Functional Coupling
- When two or more modules share responsibility for business logic or rules they are functionally couple because any change to that business logic will affect all modules that share these responsibilities.
- Functional coupling is not all or nothing and be further divided into the following types based on the extent of shared knowledge including:
    1. Sequential Functionality - Similar to the connascence model of temporal coupling, this type of functionality requires things to run in a specific order for the business process to work.
    2. Transactional Functionality - When there are multiple operations that must be carried out as part of a single unit of work.  One failure at any point requires a rollback of all operations within the transaction.
    3. Symmetric Functionality - Multiple modules implementing the same functionality that must be updated synchronously for any business requirements changes, otherwise risking an invalid system state.  Don't violate the DRY principle!
- Functional example: If two services are sharing the same database and they read/write data to the same table they must follow the same business rules to ensure consistency of data and are therefore functionally coupled.
- An effect of functional coupling is that shared knowledge implemented separately by modules results in relationships that are implicit and difficult to track which can result in unintended system behavior if changes are not implemented in tandem.

##### Model Coupling
- This type of coupling is when multiple modules use the same model of a given business domain.
- Models could represent the same object in different fashions for different needs (i.e. the support case for case management vs BI).  Creating one model for all needs could create an overly complex object that will likely cross module boundaries.
- Functional example: If Service A is responsible for reading/writing to it's database but that database is shared with Service B via a readonly interface that would indicate model coupling.
- Unlike __functional coupling__, model coupling only shares models as a means of integration and no functionality is shared between the modules.  This can still create breaking changes if the model requires updates for new business logic.

##### Contract Coupling
- When modules use an integration specific model, or contract, to communicate between each other.  It is an agreement outlining the terms of collaboration for the integrated modules.
- Contract coupling shares the same degrees of coupling as __model coupling__ through levels of static connascence.  However, the strongest form of contract coupling is less prone to cascading changes than the weakest form of __model coupling__ because the model is related to implementation details while an integration contract is not.
- Functional example: If Service A and Service B communicate to the same database using an integration model that would be considered contract coupling since both services use an abstracted contract to integrate via the database.
- The use of an integration model reduces the risk of cascading change and creates and explicit integration method.  Despite it's numerous advantages we should think of contract coupling as another tool in the toolbox and not the absolute end goal.

##### Integration Strength Discussion
- The stronger the integration between modules the more likely it is that changes will have ripple effects for integrated modules and the less predictable the effects will be.
- Coupling strength defines the type of integration interface while the degree describes the complexity of the information communicated through that interface.
- Asynchronous execution alone does not reduce coupling as there are many aspects of coupling that could be present in asynchronous communication depending on the implementation.

#### Chapter 8 - Distance
- The larger the distance is between multiple components that have shared knowledge and thus need to change together, the greater the level of effort required to implement that change.
- The greater the distance for co-evolving modules the heavier the cognitive load and the more likely someone is to forget to update one of the components at some point.

> "Distance between components is inversely proportional to their lifecycle coupling."

- Collateral changes can occur when functionality that is unrelated in a component, violating the single responsibility principle, must be tested and deployed because they are lifecycle coupled.
- There is also a socio-technical component to consider for distance. Does the same engineer own 2 things that are coupled?  Different teams in the same department?  Different departments?  Are they located in the same time zone?  The further the socio-technical distance the more collaboration required for shared knowledge changes.
- Runtime couple is determined by how two modules communicate with eachother, meaning the more syncrhonous the communication the higher the runtime coupling and the more asynchronous the communication is the lower the runtime coupling.
- Shared knowledge indicates how likely two modules are to change together, the distance of those modules determines the cost of coordinating those changes.

#### Chapter 9 - Volatility
- Coupling that is not ideal in theory may not be a major concern if the system is static, the less a system changes the less these complex interactions create problems.

##### Why Software Changes
- There are 2 areas that software design revolves around, the problem space and the solution space.
- The problem space defines the business problem that needs to be solved by the software.
- The solution space is all about the software itself and how it is designed, architected, and implemented.

**Solution Changes**
- The solutions to a problem can change without the problem itself changing.
- Sometimes solutions change as the result of organizational changes (the effect of Conway's Law).
- It's important to note that organizational distance is not necessarily physical, teams that are distant organizationally may not be physically distant but communication channels would be more "distant" depending on if they are in the same team, or different departments.

**Problem Changes**
> "Walking on water and developing softwar efrom a specification are easy if both are frozen." - Edward V. Berard
- New functionality might be required because new business insights, opportunities, or customer demands arisse.

##### Evaluating Rates of Changes
- Business Domain - The overall area of activity in which a business operates.
- Business Subdomains - Finer-grained areas of the business that are focused on specific parts of business activity that are needed for the company to succeed in its business domain.
**Types of Subdomains**
1. Core - This subdomain contains key functionality that gives the company a competitive advantage in their business domain.  These subdomains are expected to be the most volatile.
2. Generic - These are the oppositive of core subdomains and may even leverage out of the box solutions that your direct competitors use.  
3. Supporting - Somewhere between core and generic subdomains.  While they offer no competitive advantage because the barriers to entry are generally low and easy to overcome, they are not able to be solved with pre-existing solutions.

#### Chapter 10 - Balancing Coupling
- There are 3 dimensions that we use to measure coupling between modules: strength (or shared knowledge), space (or physical arrangement), and time (or volatility)
- The goal is not to minimize the strength of coupling in our designs, but to design a modular system that is simple to implement, maintain, and evolve which means we must consider all 3 dimensions.

##### Measurement Units
- VOLATILITY AND STRENGTH - Both volatility and strength are high
- NOT STRENGTH OR NOT DISTANCE - Strength is low or distance is low, or both are low
- VOLATILITY XOR DISTANCE - Either one of volatility and distance is high, and the second is low

##### Stability: Volatility and Strength 
STABILITY = NOT(VOLATILITY AND STRENGTH)

##### Actual Costs: Volatility and Distance
CHANGE COST = VOLATILITY AND DISTANCE

##### Modularity and Complexity: Strength and Distance
MODULARITY = STRENGTH XOR DISTANCE
COMPLEXITY = NOT MODULARITY
           = NOT (STRENGTH XOR DISTANCE)
LOCAL COMPLEXITY = NOT STRENGTH AND NOT DISTANCE
GLOBAL COMPLEXITY = STRENGTH AND DISTANCE

##### Combining Strength, Distance, and Volatility
MAINTENANCE EFFORT = STRENGTH * DISTANCE * VOLATILITY

BALANCE = NOT (COMPLEXITY AND VOLATILITY)
        = MODULARITY OR NOT VOLATILITY
        = (STRENGTH XOR DISTANCE) OR NOT VOLATILITY

##### Balancing Coupling on a Numeric Scale
> DISCLAIMER: THIS IS NOT AN EXACT SCIENCE!

**Scale**
- Integration Strength
    - 1 = Contract coupling
    - 3 = Model coupling
    - 8 = Functional coupling
    - 9 = Symmetric functional coupling
    - 10 - Intrusive coupling
- Distance
    - 1 = Methods in the same object
    - 2 = Objects in the same namespace/package
    - 3-7 = Objects in different namespaces/packages
    - 8 = Different libraries
    - 9 = Services in a distributed system
    - 10 = Systems implemented by different vendors
- Volatility
    - 1 = Legacy system that is not being evolved
    - 3 = Supporting or generic subdomain
    - 10 = Core subdomain, or inferred volatility from a core subdomain
    
#### Chapter 11 - Rebalancing Coupling

Change is inevitable in software, it evolves and adapts to meet new business requirement and solve new problems.  When change is introduced it can sometimes be accommodated by the existing design, and sometimes it cannot.  When it cannot it's important to review previous design discussion and see what assumptions these new changes might have exploded.

##### Software Change Vectors
- Tactical Changes - These will alter the way a system or it's components support business goals and can be anticipated.  This means that adequate software design should be able to accommodate these changes.
    - These changes can also involve bug fixes and other implementation improvements.
    - If changes don't require adjusting existing component boundaries or their interrelationships they are considered tactical changes as well.
- Strategic Changes - These are more substantial and shift what's being implemented, what problems you're solving, or what org/structure executes it.
    - **Functional Requirements** - This would be the expansion of functionality with new knowledge that can reshape the existing design.
    - **Business Strategy** - When subdomains shift and the core subdomain of an organization requires a different software approach.
    - **Organizational Changes** - As organization grow or re-organize and change communication patterns software will follow those organizational changes.
    - **Environmental Changes** - Things like execution environment or regulatory shifts can constitute environmental changes that require significant software change.

##### Rebalancing Coupling
> "Contrary to tactical changes, which are supposed to fit within the software's design, strategic changes can disrupt both design and the assumptions it was built upon.  As a result, the three dimensions of coupling--strength, distance, and volatility--have to be rebalanced to ensure the system's modularity in the long term."

#### Chapter 12 - Fractal Geometry of Software Design
- Growth is natural, and even good, for software systems and are usually due to things like growing requirements as business value is proven out or increased scaling for expanding user bases.

**Network-Based Systems** - Geoffery West characterized network based systems by having the following properties:
    1. Space filling: The system sustains itself by transporting energy through a hierarchical branching network, ensuring that the energy reaches all parts of the systems.
    2. Invariant terminal units: The energy is delivered to terminal units, which maintain consistent size and characteristics regardless of the overall size of the system.
    3. Optimization: The system continuously evolves to minimize energy wastage and maximize available energy.

**Software Design as a Network-Based System** - Similarly, software systems are network-based systems and are evident in the properties that define them:
    1. Space filling: While knowledge can change its form, it ultimately reaches all components of a system: from high-level modules all the way down to the machine code instructions executed at the system's lowest levels.
    2. Invariant terminal units: In the end, all knowledge communicated across a system's modules is translated into machine code instructions.  Regardless of system size, the machine code and the hardware executing it remain the same.
    3. Optimization: They network delivering knowledge, represented by the design of component boundaries, can be optimized.  This optimization reflects the process of improving a system's design and evolving its functionality.

- Systems that increase typically find efficiencies of scale
- There are limits to this growth because not everything that becomes more efficient has a positive impact
- The hard limit is imposed when the negatives of the growth outweigh the positives of their own growth and break "under their own weight"
- Extending an existing system with new functionality has a couple of things to weigh for balance
    1. Assuming the new functionality can be somewhat built on existing parts of the system, if the functionality is doubled the required knowledge is not because some existing knowledge is also used for the new functionality
    2. Assuming each new module must talk to every other module (overstated yes, but illustrates the point) the lines of communication scale superlinearly and increase the complexity of the system until the cognitive overheard of the system is unbearable
- This does not mean that there are certain ceilings that a system cannot grow beyond, at a certain point though they require innovation in the way of strong material or change in form and proportions

#### Chapter 13 - Balanced Coupling in Practice

##### Case Study 1: Events Sharing Extraneous Knowledge
- The WolfDesk Case Support Management (CSM) team published all internal events for other teams to integrate with
- The Support Autopilot team consumed these messages and trained a model to auto-generate solutions for new cases
- When the SCM team added new events or modified existing ones that created friction for the Autopilot team because they needed to retrain the model
- Since the Autopilot team was consuming all of the different event types there was "model coupling" between distant systems
- Addressing the issue required creating 2 event types; private events that would be used internally by the service to model the lifecycle of the support cases, and public events that act as an integration specific model that exposes minimum required information to shift the communication style from "model coupling" to "contract coupling" which is a more appropriate communication style for distant components

##### Case Study 2: Good Enough Integration
- The Desks component manages the help desks, organizational units, and agent schedules
- This is a supporting subdomain as it does not offer a competitive advantage
- The Distribution component relies on the Desks component schedule changes which is also considered "model coupling"
- Even though this is the same communication style as Case Study 1 it does not cause integration issues because the Desks component does not change so the reduced volatility means less friction

##### Case Study 3: Reducing Complexity
- The original design by the WolfDesk team was a layered approach where each layer was responsible for a portion of the app (i.e. presentation, application, business logic, and data access layers)
- This means there is model coupling up and down the layers and implementing changes requires touching all layers
- Instead they switched to a vertical slices approach, focusing on breaking the application down by functions instead of layers
- This allows the team to keep closely related code together and reduce cascading changes

##### Case Study 4: Layers, Ports, and Adapters
- Despite changing to vertical slices and layers the team was still running into difficulties with changes to the Support Cases Lifecycle slice
- To solve this challenge the team adopted the ports and adapters architecture (Cockburn 2005) which inverts the dependencies
- The Domain becomes the top layer which feeds into the application layer which then feeds into the infrastructure layer
- This inversion creates additional distance between components and shifts the coupling to model or contract coupling which increases modularity

##### Case Study 5: Entities and Aggregates
- There are initially 4 classes in the WolfDesk functionality including: SupportCase, Message, Customer, and SupportAgent
- The ORM implemented allows the engineers to traverse freely between cases, customers, messages, and support agents
- A requirement for a case to be escalated if no message response is sent by an agent within a time window introduces the need to atomically commit changes between messages and cases to enforce this new rule
- By using the aggregate pattern (Evans 2004) we can limit the object traversal to functionally coupled objects (i.e. messages and cases) and only store the Ids for the agent and customer

##### Case Study 6: Organizing Classes
- Originally the team decided to organize files in folders according to the technical roles they play
- This resulted in the same problem as Case Study 4 where related items would be located in distant folders
- By co-locating items within the same folder based on functional coupling you can minimize the distance between them and reduce the cognitive load of where those related files live

##### Case Study 7: Divide and Conquer
- In the original SupportCase class models in Chapter 8 it implemented a send email and send SMS notification method
- We moved that out to the domain layer and defined an new class for handling those communications
- We can further create distance between these modules by extracting each method into its own interface

##### Case Study 8: Code Smells
- Look for functionality that should be shared to lift it out into a more centrally accessible location
- Reduce dependency on things that are not closely related
- Don't overshare knowledge between components and modules when unnecessary
- Relocate code to be near the things that they are functionally coupled with or share knowledge with
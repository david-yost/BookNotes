# Team Topologies

## Organizing Business and Technology Teams for Fast Flow

#### by Matthew Skelton and Manual Pais

## Part 1: Teams As The Means Of Delivery

### Chapter 1: The Problem With Org Charts

> "Organizations should be viewed as complex and adaptive organisms rather than mechanistic and linear systems." -Naomi Stanford, Guide to Organisation Design

- We should stop looking at teams as collections of interchangeable individuals that will succeed as long as the use the "right" processes and "right" tools.  Instead we should treat people and technology as a single human/computer sociotechnical ecosystem.
- Communication lines are often different than reporting lines of an org chart.
- Systems thinking focuses on optimizing the whole, looking at the overall flow of work, identifying what the largest bottleneck is todasy, and eliminating it.  Then repeat.
- Similar to how architecture diagrams are usually stale soon after work starts, org charts are usually out of sync with reality.

**Three different organizational structures**
1. Formal structure (the org chart) - facilitates compliance
2. Informal structure - the "realm of influence" between individuals
3. Value creation structure - how work gets done based on inter-personal and inter-team reputation

- Team topologies abandons the historically static organizational structure in favor of an adaptable model that suits the current situation.

**Team Topologies provides four fundamental team types**
1. Stream-aligned
2. Platform
3. Enabling
4. Complicated-subsystem

**Team Topologies provides 3 core team interaction modes**
1. Collaboration
2. X-as-a-service
3. Facilitating

> "Organizations which design systems...are constrained to produce designs which are copies of the communications structures of these organizations." -Conway's Law

- When a team's cognitive load isn't considered, typically the team ends up spread thin, being tasked with excessive responsibilities and domain ownership.  This leads to a lack of mastery and lengthened context switching timelines.
- Too many team responsibilities also is antithetical to Dan Pink's three elements of intrinsic motivation: autonomy (juggling too many requests and priorities for other people), mastery (being a "jack of all trades, master of none"), and purpose (too many domains of responsibility).

### Chapter 2: Conway's Law and Why It Matters

#### Understanding and Using Conway's Law

- Alan MacCormack and his colleagues from Harvard Business School studied some open and closed source software products and discovered strong evidence that product architecture tends to mirror the structure of the organization that developed it.
- Studies in other industries have also corroborated that Conway's law often applies even to non software organizations and has been seen evidenced in vehicle manufacturing and aircraft engine design.

> "If the architecture of the system and the architecture of the organization are at odds, the architecture of the organization wins." - Ruth Malan

> "Given any \[particular\] team organization, there is a class of design alternatives which cannot be effectively pursued by such an organization because the necessary communication paths do not exist." - Conway

#### The Reverse Conway Maneuver

> "Our research lends support to what is sometimes called the 'Inverse Conway Maneuver,' which states that organizations should evolve their team and organizational structure to achieve the desired architecture.  The goal is for your architecture to support the ability of teams to get their work done--from design through deployment--without requiring high-bandwidth communication between teams." - Accelerate The Science of Dev Ops

#### Software Architectures that Encourage Team-Scoped Flow

> "Team assignments are the first draft of the architecture." - Michael Nygard

Proven software-architecture good practices to consider when building teams that will drive architecture
- Loose coupling - components do not hold strong dependencies on other components
- High cohesion - components have clearly bounded responsibilities and their internal elements are strongly related
- Clean and appropriate version compatibility
- Clear and appropriate cross-team testing

#### Organization Design Requires Technical Expertise

- Accepting Conway's Law also means that we must acknowledge that anyone making organizational decisions also has a huge effect on the resulting architecture of a system.

> "More than ever I believe that someone who claims to be an Architect needs both technical and social skills, they need to understand people and work within the social framework.  They also need a remit that is broader than pure technology--they need to have a say in organizational structures and personnel issues, i.e. they need to be a manager too." -Allan Kelly

#### Restrict Unnecessary Communication

- Not all communication and collaboration is a good thing, we need focused communication between specific teams.
- The goal of any organizational structure should be to minimize the number of communication paths between teams.
- In an in-person setting you could use something as simple as locational proximity in the office to restrict communication artificially.

#### Beware: Naive Uses of Conway's Law

- Don't solely focus in on architectural structure, fast flow is also something that should be considered to optimize team efficiency.
- Shared communication tools can also be a powerful driver of self-similar design.

### Chapter 3: Team First Thinking

> "Disbanding high-performing teams is worse than vandalism: it is corporate psychopathy." Allan Kelly

- According to Google's own internal research, who is on the team matters less than the team dynamics; and according to performance measurements teams matter more than individuals.

#### Use Small, Long-Lived Teams As The Standard

- Team - defined by this book as a stable group of five to nine people that work towards a shared goal as a unit.
- Alternatively, team size has been defined by Amazon as however many people can be fed by two pizzas.
- Allowing teams to grow larger than that size risks the teams viability of producing solid software because trust begins to break down and less than ideal decisions can follow.

> NOTE: In cultures that have an incredibly high level of trust the team size rule can be more flexible, however, very few organizations fit this criteria.

#### Smaller Size Fosters Trust

- There are natural limit's to the depth of relationship we can have with people in groups according to Dunbar's anthropological research.
    1. Around five people - limit of people with whom we can hold close personal relationships and working memory.
    2. Around fifteen people - limit of people with whom we can experience deep trust.
    3. Around fifty people - limit of people with whom we have mutual trust.
    4. Around one hundred fifty people - limit of people whose capabilities we can remember.

- In addition to individual teams, it's also important to limit team groupings to make sure the size of a grouping does not exceed the anthropological capacity for trust.
    1. A single team: around five to eight people (base don industry experience), in high-trust organizations no more than fifteen people.
    2. Families (tribes): groupings of teams of no more than fifty people, or in high-trust organizations one hundred fifty people.
    3. Divisions/streams/profit & loss (P&L) lines: groupings of no more than one hundred fifty or five hundred people.
- When these upper thresholds are reached we need to split off another unit as a self-independent group.
- Splitting off another unit often means that teams need to be realigned to consider the software architecture of the new groups, also known as "team-first architecture".

#### Work Flows to Long-Lived Teams

- It can take between 2 weeks and 3 months for a team to become a cohesive unit which makes stability important!
- Teams should be stable, but not static, changing occasionally but only when necessary.
- In Tuckman's Team Development model storming is the second step on the path to performing, however recent research indicates that teams will often go through multiple stages of storming.

#### The Team Owns the Software

- Small teams that are long lived give a stable group of engineers a greater sense of ownership over the code.

TODO: Finish Chapter 3 starting on page 36

## Part 2: Team Topologies that Work for Flow

### Chapter 4: Static Team Topologies

- The most common way to setup teams today is focused on immediate needs rather than the ability to adapt in the long run.
- Two common anti-patterns are ad hoc team design, where teams are broken up when they get too large and communication overhead takes a toll, and shuffling team members, where teams are rapidly assembled for projects then disassembled.
- When considering team flow it's important to consider communication lines and try to minimize "Handovers"
- DevOps Topologies reflect two key ideas:
    1. There's no one size fits all approach to structuring teams for DevOps success.
    2. There are several topologies known to be detrimental to DevOps success.

> The Success of different types of teams does not depend solely on team member's skills and experience; it also depends on (perhaps most importantly) the surrounding environment, teams, and interactions.

> A lack of ownership over shared code may result from the cumulative effects of several teams working on the same codebase unless inter-team discipline is high.

- Removing hard dependencies between teams allows product teams to operate more autonomously (i.e. cloud team designs cloud infrastructure process, product teams then can provision and update application resources)
- An error budget is essentially defined by the SRE team as an acceptable amount of down time.
- SRE is "what happens when you ask a software engineer to design an operations function." according to Ben Treynor, the VP of Engineering at Google.
- The relationship between the SRE team and the application team changes as an application scales up and down based on how much traffic the site has and how much support the team needs in keeping it stable and running.

#### Considerations When Choosing a Topology

1. Technical and cultural maturity - How strong is the engineering discipline in the organization and what disciplines are missing?  Implementing a new discipline, like DevOps, risks creating more silos in the organization if not correctly handled.
2. Organization size, software scale, and engineering maturity - Engineering maturity moves from specialized to end to end ownership as your organization goes from low to high on that scale while org size/software scale moves from more regular and strong collaboration to more ownership and reliability.
3. Splitting responsibilities to break down silos - If a team is too large or has too many responsibilities it can make sense to split those responsibilities into smaller more explicit areas (i.e. database team gets split to DBA and DB Dev).
4. Dependencies and wait times between teams - Track dependencies with dependency tags to surface dependency bottlenecks and allow you to track them.  If those dependencies exceed a certain threshold that should trigger team design adjustments.

### Chapter 5: The Four Fundamental Team Topologies

- Making sure the right teams are in place, all capabilities are being addressed, teams have necessary autonomy and support becomes simpler if we focus on four fundamental team topologies: Stream-aligned team, Enabling team, Complicated-subsystem team, and Platform team
- Reduced ambiguity around organizational roles is a key part of success in modern organizational design
- Ops and support teams do not exist as a separate function and should be aligned to streams

#### Stream aligned teams
- A "stream" is the continuous flow of work aligned to a business domain or organizational capability
- Stream aligned teams are aligned to a single, valuable stream of work which could be a product, service, set of features, user journey, or user persona
- They should be empowered to build and delivery customer/user value as quickly, safely, and independently as possible
- Other fundamental team topologies serve the purpose of reducing burdens on stream aligned teams
- Capabilities for a stream aligned team to operate independently include, but are not limited to: Application security, commercial and operational viability analysis, design and architecture, development and coding, infrastructure and operability, metrics and monitoring, product management and ownership, testing and quality assurance, user experience (UX)
- Stream aligned teams can be product teams, but products can be larger than an individual team or sometimes software does not need products or features, however all software benefits from alignment to flow

##### Expected behaviors for stream aligned teams
1. Aims to produce a steady flow of feature delivery
2. Quick to course correct based on feedback from the latest changes
3. Uses an experimental approach to product evolution, expecting to constantly learn and adapt
4. Minimal (ideally zero) hand-offs of work to other teams
5. Evaluated on the sustainable flow of change it produces
6. Must have time and space to address tech debt
7. Proactively and regularly reaches out to the supporting fundamental-topologies teams
8. Members feel they have achieved or are in the path to achieving "autonomy, mastery, and purpose"

#### Enabling teams
- An enabling team is composed of specialists in a given technical or product domain and help bridge capability gaps on the stream aligned teams
- They research, try out options, and make informed suggestions on adequate tooling, practices, frameworks, and any other ecosystem choices around the application stack
 
 TODO: Finish chapter 5 notes starting from page 87

### Chapter 6 - Choose Team-First Boundaries

- Many problems that arise in delivering software come from poorly defined boundaries or areas of responsibility between highly coupled teams.

#### Types of monoliths

1. Application Monolith - A single large application with many dependencies and responsibilities that is deployed all at once and the system is unavailable during deploy.
2. Joined-at-the-database Monolith - Several applications that are all sharing the same database schema, making it difficult to test and release new changes separately.
3. Monolithic Builds (Rebuild Everything) - One massive CI runs the build for everything every time instead of standard dependency management mechanisms like packages or containers.
4. Monolithic (Coupled) Releases - Services that can be built separately but must be deployed with dependent services in a static environment together.
5. Monolithic Model (Single View of the World) - This is a software model that forces a single domain language and format across many different contexts.
6. Monolithic Thinking (Standardization) - A "one size fits all" approach that puts restrictions on what technologies teams can use and how they can use them in an attempt to minimize variation.
7. Monolithic Workplace (Open-Plan Office) - An open office floor plan where everyone is in the same geographic location with workspaces separated by cubicles or barriers.  Colocation of purpose is what's important, not colocation of bodies.

#### Fracture Planes

> A fracture plane is a natural seam in the software system that allows the system to be split easily into two or more parts.

- It is usually best to align software boundaries with the different business domain areas.

##### Types of Fracture Planes

1. Fracture Plane: Business Domain Bounded Context - The boundaries should be defined by a business-domain bounded context.

> "a concept may appear to be atomic just because we have a single word to cover it.  Look hard enough and you will find seams where you can fracture that concept." - Michael Nygard

2. Fracture Plane: Regulatory Compliance - Highly regulated industries with standards that are dictated for compliance.  It can make sense to break of a regulatory compliance focused team (credit card payment focused for instance) that focuses specifically on the compliance concerns that don't need to impact the rest of the application.

3. Fracture Plane: Change Cadence - When different parts of a monolith are updated at different rates you can split out areas of functionality based on how often they need to be released.  Quarterly monthly reports do not need to hold up other fixes and enhancements that can be delivered daily or weekly.

4.  Fracture Plane: Team Location - Splitting up teams and their functional focus based on their location.  Time Zones are one of the most important considerations but being physically present in the same office space or fully remote with standardized communication channels for all are the 2 best approaches.

5.  Fracture Plane: Risk - Looking for areas that have disparate risk profiles is another way to approach splitting things up.  Some areas of the application may have higher risk due to regulatory concerns or the size of user based that rely on it.

6. Fracture Plane: Performance Isolation - Areas of an application that may require a high degree of resilience and scalability can be split off from application segments that are more stable.

7. Fracture Plane: Technology - When technology is older and less automation friendly and needs specialized skills or testing it can be a good dividing line. Also, when a technology is different enough from the rest of the tech stack that removing it can significantly reduce the cognitive complexity for a team.

8. Fracture Plane: User Personas - Finding dividing lines for application functionality based on sets of users.  For instance a free tier user vs a paid subscription user, or a novice user vs an expert level user.

- Does the resulting architecture support more autonomous teams and less cognitive load?
- Could we as a team, effectively consume or provide this subsystem as a service?

## Part 3: Evolving Team Interactions for Innovation and Rapid Delivery

### Chapter 7 - Team Interaction Modes

- Poorly defined team interactions can be a source of friction and ineffectiveness.
- Sometimes teams move in and out of communication modes and when considering relationships between a team it's important to know how collaborative or disconnected they should operate.

> A study done by researchers found that teams that interacted intermittently, intermittently instead of constantly, not only ended up with similar quality solutions but also found better solutions than teams that constantly interacted.

#### The Three Essential Team Interaction Modes

1. Collaborative - working closely together with another team
2. X-as-a-Service - consuming or providing something with minimal collaboration
3. Facilitating - helping (or being helped by) another team to clear impediments

- A medium-large sized company likely requires all three modes of communication and it's often earlier than most people would expect.
- Defining the ways that teams should interact makes it easier to assess how effective they are being in those interactions and the software interfaces should reflect that in design.
- Modes of interaction should become habits in the teams.

##### Collaboration

- Suitable when a high degree of adaptability and/or discovery is needed, especially when exploring new techniques or technologies.
- Can be used for two teams with distinct expertise and responsibilities working together on a small set of things.
- Alternatively, the two teams working together can pool their resources and expertise together to create essentially one big team (must not exceed Dunbar's number of fifteen).
- Both teams must always focus on a small defined overlap with a full overlap of focus and responsibilities.
- Working in a larger area with more people means expanding the surface area of cognitive complexity and the requirement of additional communication, which means the slow down in effectiveness should be outweighed by the rapid discovery in order to make it valuable.

##### X-as-a-Service

- Most applicable to situations where there is a need for one or more teams to use a code library, component, API, or platform.
- Teams should be able to rely on certain aspects of their technology landscape being provided as a service by other teams (internal or external) so the team can focus on delivering their work.
- Creates clear boundaries which inherently reduces cognitive load for the teams building and consuming.
- Changes happen slowly over time with a clean API that is well defined and stable.
- Teams involved have little need for day-to-day collaboration to use or provide the X-as-a-Service feature.
- This model only works well with a well chosen an implemented service boundary and good service management.
- A team providing X-as-a-Service must have a strong sense of responsibility towards its consumers and provide straight forward to use documentation and be managed in a way that keeps it viable over time.

##### Facilitating

- Suitable for situations where one or more teams would benefit from active help of another team that is facilitating or coaching some aspect of their work.
- This is the primary mode of operation for an enable team that provides support and capabilities to other teams.
- Typically facilitating teams work across many teams at once to detect cross team problems and help reduce them.
- These teams do not spend time building the main software systems but look for ways to improve the quality of interactions between each other.

#### Team Behaviors for Each Interaction Mode

> Promise Theory - Mark Burgess defines this mode of team relationships in opposition to commands and enforceable contracts.  In the example of semantic versioning you're promising not to break software that depends on your code.

- High Interaction and Mutual Respect (Collaboration Mode): Use techniques like, pair programming, mob programming, and white board sketching.  Also be aware that boundary-spanning can lead to somethings taking longer to work through with a large surface area of cognitive complexity due to the combining of the domain areas.
- Emphasize the User Experience (X-as-a-Service Mode): Training or coaching in UX and DevEx can be key to helping teams understanding how to produce the most fruitful interactions for the teams consuming their product.
- Help and Be Helped (Facilitating Mode): Training or coaching for teams on how to receive help or insights from teams that might have discovered a better way to do something they're doing.

Team interaction modes of the fundamental team topologies
|                        | Collaboration | X-as-a-Service | Facilitating |
| ---------------------- | ------------- | -------------- | ------------ |
| Stream-aligned         | Typical       | Typical        | Occasional   |
| Enabling               | Occasional    |                | Typical      |
| Complicated-subsystem  | Occasional    | Typical        |              |
| Platform               | Occasional    | Typical        |              |

#### Choose Team Interaction Modes to Reduce Uncertainty and Enhance Flow

-  Collaboration mode can be used to discover viable X-as-a-Service boundaries or redefine those boundaries until the interfaces are proven to be stable and functional.
-  If a team interaction has become stale or needs revitalized it may make sense to temporarily change the mode of team interaction to help team members refresh and grow.
-  If interactions between teams feel awkward, forced, or cumbersome it could be because there is missing capabilities or misplaced boundaries between them.

> "We need to be alert for the white space between the roles, gaps that nobody feels responsible for." - Don Reinersten
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


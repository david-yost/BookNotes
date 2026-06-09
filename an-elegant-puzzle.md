# An Elegant Puzzle

## Systems of Engineering Management

#### by Will Larson

### Chapter 1 - Introduction
- Many reasons exist for why ICs become managers ranging from idealistic to spiteful, but the necessary tools for managing successful are the same
- There are few things peaceful about managing in a rapidly growing company but the author thinks this is one of the best environments to learn and grow
- The following chapters are broken into topical themes such as; organizations, tools, approaches, culture, and careers

#### Chapter 2 - Organizations
- It can be difficult to understand why some organizations create energy while others create friction, frustration, and politics
- When you have a problem that needs solved quickly and cheaply start thinking process design
- When you have a problem that needs solved permanently and you have time to go slowly start thinking about how to evolve your culture
- If process is too week and culture is too slow, organizational design lives between those two

##### 2.1 Sizing Teams
- The fundamental challenge of organizational design is sizing teams
- There is no universal law for right-sizing teams but here are a few guiding principles that are useful
> 1. Managers should support 6 - 8 engineers
> - Tech Lead Managers (TLMs) - managers with less than 4 engineers that take on design and implementation work leaving not enough time to progress as a manager and not enough time to progress as a staff engineer
> - Coaches - managers with more than 8 or 9 engineers act as coaches and safety nets for problems because they can't spend enough time investing in their teams
> 2. Managers of managers should support 4 - 6 managers
> - Ramping up - managers supporting less than 4 managers should be in a period of active learning on problem domains or transitioning engineers to supporting managers
> - Coaches - same problem as before, supporting too many managers leaves you functioning in a purely problem solving coach mentality
> 3. On-call rotations want eight engineers
> - Shared rotations - when a team is not large enough to have 8 engineers to support an on-call rotation you can pool multiple engineering teams together to meet that threshold, but note that this is not great long-term because it requires engineers to be on-call to support something they're not as familiar with
> 4. Small teams (fewer than 4 members) are not teams
> - An important aspect of teams is the abstraction from the complexities of the individual that makes up a team and below a 4 person team that becomes indistinguishable 
> - Keeping innovation and maintenance together - avoid the temptation to split innovation and maintenance into separate teams, keeping these in the same team gives you a higher morale and culture of learning while avoiding a two-tiered class system of innovators and maintainers

**Fitting together those guiding principles here's the simple and effective playbook:**
1. Teams should be 6 - 8 during steady state
2. To create a new team, grow an existing team to 8 - 10, and then bud it into 2 teams of 4 or 5
3. Never create empty teams
4. Never leave managers supporting more than 8 individuals

##### 2.2 Staying on the path to high-performing teams
- Hiring new engineers is not necessarily always the answer for a growing organization, here's a loose framework to determine what a team needs to increase performance
- Falling Behind? Add People -> Treading Water? Reduce WIP -> Repaying Debt? Add Time -> Innovating? Add Slack

**Four states of a team**
1. A team is falling behind if each week the backlog is longer than it was before
2. A team is treading water if they complete critical work but can't pay down tech debt or begin new major project work
3. A team is repaying debt when they're able to pay down tech debt and benefit from it
4. A team is innovating when tech debt is low, morale is high, and the bulk of work is satisfying users

**System fixes and tactical support**
How to we support the teams in various states of transition?
1. When the team is falling behind the fix is to hire more people until the team moves to treading water. Provide support by setting expectations with users, finding easy wins, and providing optimism.
2. When the team is treading water the fix is to consolidate their efforts to finish more things and reduce concurrent work until they can repay tech debt.  Tactical support here focuses on helping people transition from a personal view of productivity to a team view.
3. When a team is repaying debt the fix is to add time.  Tactically try to find ways to support users while also repaying debt so you don't disappear from your users' perspective.
4. Innovating the fix is to constantly create enough slack in the team's schedule to build quality into their work and continue to operate innovation and avoid taking a step backwards.  Tactical support is making sure the innovation the team is doing is bringing business value so it doesn't seem like they're just running useless science experiments.

##### 2.3 A case against top-down global optimization
- It's a common response to question if engineers that were involved paying down tech debt as a team should move onto other teams once they feel like they're in a good spot and those individuals might be seen as "excess resources"
- **Team First** - Sustained productivity comes from high performing teams nad we should be hesitant to disassemble a team that is productive.
- **Fixed Costs** - Most teams have high fixed costs and relatively small variable costs and moving one person can shift an innovating team back into falling behind.
- **Slack** - Do not add more resources to a team with visible slack, but the inverse doesn't necessarily apply.  Expected time to complete a new task approaches infinity as a team's utilization approaches 100 percent.
- **Shift scope; rotate** - Sometimes moving scope between teams is a far more useful approach than shifting people.  You can maintain the developed jelling of the team while right-sizing their responsibilities.  Alternatively you can rotate someone to an area in need temporarily which also has the added benefit of testing how much slack that team actually has.

##### 2.4 Productivity in the age of hypergrowth
- When an organization is growing so quickly that it feels like a new company frequently because of all of the new additions it can be difficult to keep process in line for your size

**More engineers, more problems** - Productively integrating large numbers of engineers is difficult, and depending on how long it takes for them to ramp up you can find your untrained engineers increasingly outnumbering the trained ones.  There are also additional overhead commitments that come along with this such as:
- More time involved training new engineers
- Interview overhead for finding new engineers
- Team growth, creation, and management
- More commits, deployments, and outages to manage through
- More teams means more coordination overhead

**Systems survive one magnitude of growth** - There are a few important trends when understanding the overall impact of increased load:
1. Most systems are designed to support one to two orders of magnitude from their current load.
2. If you traffic doubles every six months, then your load increases an order of magnitude every 18 months.
3. The cardinality of supported systems increases over time as you add teams, and as "trivial" systems go from unsupported afterthoughts to focal points for entire teams as the systems reach scaling plateaus.

> "If your company is designing systems to last one order of magnitude and is doubling every six months, then you'll have to re-implement every system twice every three years."

**Ways to manage entropy** - Finishing projects can be hard with all of the other demands that consume your time.  Here's a few things to mitigate that demand.
- When the company grows, you can't stop it but you can focus that growth.  Allow teams to alternate between periods of rapid hiring and consolidating and jelling.
- If engineers are often interviewing, say three times a week, give them a month off every three or four months.
- Find ways to limit ad hoc interruptions by funnelling them to a small area and increasingly automate that area.  Once you have a rotation of folks in place to respond to these train your team not to answer other forms of interruptions.
- Create an ownership registry to eliminate the running down of "who owns thing X" for on-call folks that need to respond to something.
- Build flexible systems with generic interfaces to help mitigate the migrations that might be necessary with scaling system rewrites.
- Avoid gatekeeper patterns anywhere possible.  It creates weird social dynamics and is rarely worth a human's time unless there are legal/compliance reasons or a system is deeply frail.

##### 2.5 Where to stash your organizational risk?
- This is a subset of organizational debt, the organizational sibling to tech debt, and includes things like toxic team culture, a toilsome fire drill, or a struggling leader.
- In a large organization there will likely be many of these to tackle, and typically the most successful you can be is to choose a few to focus on improving and work with the manager to set expectations.
- For the things you can't directly fix quickly, keep them close, because you _may_ be the best to manage the risk, but you're definitely the best positioned to take responsibility.

##### 2.6 Succession planning
- This is the act of thinking through how the organization would work without you.  Then you take the time and effort to document the gaps and fill them in.
- The first step is to figure out what you do, not just the things on your calendar but where are you the glue for other things someone else might not notice?  Start by looking at your roles in meetings, then look at your roles in recurring processes (i.e. roadmaps, performance calibration, headcount decisions, etc.), what individuals do you support and how, look at what categories of work are most commonly on your to-do list, and review what external relationships have been important for you in your role.
- Go through that list and identify individuals who could take on any of those items, and if someone exists cross it out.
- With the remaining gaps split them into two categories, the first being easy to close with a document or quick introduction, and the second being riskier gaps where your particular skillset is important and others maybe missing it.
- Make a plan to close all of the easy gaps and one or two of the riskier ones and add them to your personal goals.s

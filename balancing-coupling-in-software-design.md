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

#### Systems
> "A system is an interconnected set of elements organized in a way that achieves something." - Thinking in Systems: A Primer by Donella H. Meadows

- There are 3 core elements of a system as detailed by the definition above: components, interconnections, and purpose.
- Often software is a system of interconnected systems in various forms.
- Any system has a set of required components with interactions between them.
- Component design helps to explicitly decide how intergrations work as well as don't work, in a way that's meant to achieve the system's purpose.
- These interactions are what allow the system to achieve it's purpose by orchestrating the work of the components.

> "System design is inherently about boundaries (what's in, what's out, what spans, what moves between) and about tradeoffs.  It re-shapes what is outside, just as it shapes what is inside." - Ruth Malan

- To achieve modular design it's essential to remove accidental coupling while being careful and deliberate about managing essential relationships between components.
- Tolerances are introduced for mechanical engineering to set permissible limits of variation in physical dimensions because it's impossible to create everthing exactly the same every time in manufacturing.

#### Questions to Assess Shared Knowledge Across Coupled Components
- What do components need to know about other components in order to work together?  What will be the impact of a change in that shared knowledge?
- Can you identify components that have to be tested and redeployed only because they share a lifecycle with other, more volatile components?
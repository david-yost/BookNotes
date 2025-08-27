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
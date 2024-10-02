# The Emotionally Intelligent Manager

## How to develop and use the four key emotional skills of leadership

#### by David R. Caruso and Peter Salovey

## Part 1 : Learn About the World of Emotional Intelligence

### Chapter 1 - Emotions And Resoning At Work

TODO: fill out the rest of chapter 1 notes

##### Principle 6: Emotinoal universals exist, but so do specifics

- Secondary emotions, or self-concious emotions, usually have strong social or cultural components to them.
- Gender can have effects on emtions and emotional intelligence, and women have a slight advantage in the hard skills of emotional intelligence.
- Gender can also affect how actions are perceived, the same behavior could be seen as positive or negative between depending on the gender of the person taking the action.

### Chapter 2 - An Emotional Blueprint

#### Emotional Blueprint

- A schematic diagram that was created to better help us understand the emotions of a situation and to give you explicit steps to process them.
- There are 4 related skills for emotional intelligence:
    1. Read people - identify emotions: Identifying how you and those around you feel and your ability to express those feelings.
    2. Get in the mood - use emotion: Use your emotions in harmony with your thinking, use themto change your perspective.
    3. Predict the emotional future - understand emotions: Understand the emotions so you can determine what you will do.
    4. Do it with feeling - Manage emotions: Be open to your emotions and use the information to make informed decisions.
- Steps for the emotional blueprint:
    1. Identify emotions - get complete and accurate data by listening, asking questions, and paraphrasing to ensure you understand how your team feels.
    2. Use emotions - Have feelings help guide your thinking by determining how those feelings influence your thinking and the thinking of the team.
    3. Understand emotions - Evaluate possible emotional scenarios by examining the causes of these feelings and what may happen next.
    4. Manage emotions - Determin underlying, root cause and take action to solve the problem by including the rational, logical information available with the emotinoal data you just gathered to make an optimal decision.
- You must be willing to open yourself to strong feelings, both positive and negative.

## Part 2 : Understand Your Emotional Skills

### Chapter 3 - Read People, Identifying Emotions

- Being able to identify and understand emotions in yourself and those around you is the important first step in being emotionally intelligent.
- In the example of Bob, being able to read emotions that others might ignore allowed him to tune into client sentiments that were often missed, helping to saving relationships and succeed with his brash and blue collar affect in an otherwise poshed and upper-crust environment.

> Recognizing the difference between a stranger who is friendly and ready to help you and a stranger who is unfriendly and ready to attack you can spell the difference between living another day and ending up dead.

Skills for identifying emotions
1. Accurately identify how you and others feel
2. Sensing emotion in art and music
3. Expressing emotions
4. Reading between the lines
5. Detect real vs fake emotions

- Being able to accurately express your emotions, and not hide or suppress them, means that people will be able to respond more accurately to how you're feeling.
- Perceiving the emotion of someone in a situation accurately allows us to approach the situation with finesse.
- The ability to spot fake emotion versus emotions that are actually being felt is important to make sure you are accurately interpreting the situation.
- All of these components are data points that can be useful in navigating a situation's emotions.

### Chapter 4 - Get in the Mood, Using Emotions

- It is important to have access to the full range of emotions, from positive to negative, in order to fully understand and process a situation accurately.
- Being closed off to emotion is often reflected by a rigid thinking style.  
- Processing emotions accurately to evaluate a situation can lead to creative thinking and breakthrough ideas as illustrated by Julia's story.
- Not everything linking to emotion and though is emotional intelligence, it requires using these emotions to enhance and assist our thought process meaningfully.
- Nervousness and worry can be used intelligently to help you scan for threats and problem solve.
- Understanding another person's point of view can be relatively easy, but it's much harder to see and experience the world from their perspective.
- Thinking often shifts with out moods and if we are able to harness those moods we are more likely to engage in creative thinking.

> "Leadership, which embraces the emotional side of directing organizations, pumps life and meaning into management structures, bringing them to full life" - Barach, J. A., and Eckhardt, D. R. Leadership and the Job of the Executive

- Thinking does not happen without emotion, and emotion actually speeds up the decision making process tremendously.
- Alice Isen found that giving a small gift to medical students resulted with quicker and more accurate diagnosis because happy and positive emotions make us more likely to feel generous and think creatively.
- Mood-congruent memory (a.k.a. affect-dependent recall) is the phenomenon of remembering information better when in the same mood as when information was acquired.
- It is important to be aware of the various connections between emotions and cognitive processes and attempt to match emotions, whenever possible, to the work ahead or to select work for someone based on how they are feeling.

### Chapter  5 - Predict the Emotional Future, Understanding Emotions

- Problems can often stem from a misdiagnosis of the cause of people's feelings and therefore what trajectory their feelings would take as a result, as illustrated by Suzzane's story.
- Acknowledging difficult situations, or news, and having a desire to treat people honestly and fairly means being transparent in difficult times while still giving credit where you can as shown in Len's story.
- Understanding emotions takes the most though and a great deal of knowledge about what causes emotions and how they transition from one stage to another.
- Conveying emotions accurately requires us to have a rich emotional vocabulary and use it effectively.
- A common emotional equation is "if event X then emotion Y". 
- Some emotions can consist of combinations of other more simple emotions, sometimes even emotions that seem at odds with each other.
- Emotions are not static and will often develop and change as they progress.
- What-if planning can be critically important when evaluating people's emotions and how they might react to a situation, and correctly predicting the future can help us respond more adeptly.

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
 
# Use Case Diagrams

Use case diagrams can be done in a text-based fashion or in UML

## Use Cases

Use cases describe the ways a user wants to use a system--the scenarios for tasks that the user wants to successfully complete through interactions

In software development, use cases are often documented as part of system analysis for requirements

- What are the key tasks that the user is performing?
- What are successful outcomes?
- What variations are there in the tasks or their steps?
- What exceptions might occur?

## Considering User Experience

In UX oriented workflows, understanding the user and their tasks are key to writing useful and usable software  

A typical UX development process might include:

- Project analysis and planning
- User and task research (use cases and requirements)
- Interface and interaction design
- Verification and validation

Use cases help the developers maintain the user perspective

- We identify the different types of users for our system; "who" are they
- We then develop tasks for each of the different types of user; "what" will they do

## Use Cases and Actions

More formally, a user is represented by an actor
    - Each use case can have one or more actors involved
    - An actor can be either a human user or a software system

Actors have two defining characteristics: 
    - They are external to the system under design
    - They take initiative and interact with our system

During a use case, actors have a goal they are trying to achieve

Each use case describes a task or tasks for a particular actor

The description of a use case typically includes one "success" case and a number of extensions that document "exceptional" conditions

## User's Perspective and Use Cases

In use case analysis, as much as possible, we want to document scenarios from the standpoint of a user
    - Use terms related to domain-related vocabulary and concepts
    - The software system is treated as a "black box"
    - We describe inputs and expected outputs, but we avoid discussing how the system will process or produce this information

Use cases are used to capture functional requirements
    - They can be annotated for non-functional requirements and restraints

Use cases can be modeled in text-based forms or in UML use case diagrams

## Text-Based Use Cases

The use cases contain scenarios
    - A complete path through a use case from the first step to the last is called a scenario
    - Some use cases have multiple scenarios and extensions but a single user goal
    - All paths try to achieve those goals

## Developing Use Cases

Key elements:

- Short summary of system goals
- Main success scenario (system responsibility)
- Extension conditions (things to watch for or consider)
- Extension handling (decisions on policy)

Suggested order of development:

- Start: use case, goal, scope, level, actor, priority, frequency
- Think and examine: trigger, main success scenario
- Check scope: extensions, subvariations
- Finish: performance target, open issues, schedule, others

## UML Use Case Diagrams

Presents a system from the actor's (or multiple actors') point(s) of view

Includes entire flow of a scenario or operation, moving from task to task

- <include> cases: not optional, base use case not complete without it, not conditional, and doesn't change the base use case behavior
- <extend> cases: can be optional, not part of base use case, can be conditional or change behavior

Remember the WAVE test for use cases:

- W: Use case  describes WHAT to do, not how; use domain-specific (not technical) language
- A: Actor's point of view
- V: Has VALUE for actor
- E: Use case models ENTIRE scenario

## What Use Cases Provide

Analysis is the process of determining the problem, not the solution--use case analysis helps us understand what the user needs from our system so we can respond correctly

Use cases (scenarios) are at the core of the 4 + 1 architectural model, which helps look at different perspectives needed to break down a complex design into different views
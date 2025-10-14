# How Experts Design

An intuitive design approach (functional decomposition--building from pieces) is not a good way to design. Our intuitive notion of design can often lead us into trouble by oversimplifying things. Analysis and design are oversimplification of very complex tasks.

We must design pieces (classes, objects) within the context in which they must live in order to create robust and flexible systems--"complexification"

## Complexification

- In short, each part is givenits specific form by its existence in the context of the larger whole
- This is a differentiating process
- It views design as a sequence of acts of complexification; structure is injected into the whole by operating on the whole and crinkling it, not by adding little parts to one another
- In the process of differentiation, the whole gives birth to its parts: the form of the whole, and its parts, come into being simultaneously
- The image of the differentiating process is the growth of an embryo

Translation:

- Design is a process that starts by looking at a problem in its simplest terms, giving a unified whole
- It is refined by making decisions, adding information (and thus, complexity), making distinctions between elements in the design where none existed before
- But the distinctions are made within a larger context, guided by the whole
- The elements added to the domain by the decision can be guided by design patterns
- See the problem both a top-down and bottom-up view

## The Role of Patterns

Each pattern is an operator that differentiates space; it creates distinctions where no distinction was before. We have recognized "this part" of the problem and we have a pattern that might be able to give us the answer to help differentiate that part and help build the whole.

Example:

Concert tracker -> MVC (new distinction) -> View, Controller, MySQL -> DOM, Local Storage, Javascript, Rails, MySQL

This is known as progressive elaboration; each decision adds complexity in that now we have more information about the system.

## Commonality and Variability Analysis (CVA)

Well-defined patterns do not exist for all problem domains. CVA is a more general approach to OO design and can be applied to identify variation in problem domains.

You can then use design pattern principles to encapsulate that variation and protect your software from potential changes.

One key aspect of design is identifying what elements of the problem domain belong in the solution domain:
    - You need to identify the right things to model (or track) in your software
    - You want to do this as accurately as possible because the next step is to identify the relationships between those concepts
    - Once you have the relationships defined, changes to the design become more difficult

In CVA, we attempt to identify the commonalities (generic concepts) and variations (concrete implementations) in a problem domain. Such analysis will produce the abstract base classes that can be used to interface with the concrete implementations in a generic way that will enable abstraction, type encapsulation, and polymorphism. Are entities in the problem variations of one another, both variations of something else?
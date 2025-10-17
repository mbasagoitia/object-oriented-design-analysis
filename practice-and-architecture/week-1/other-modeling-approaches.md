# Other Modeling Approaches

## Working at the Conceptual Level

One of the first steps in developing an OO design is discovering the entities of the system that have responsibilities--this will turn into classes and objects. How can we determine which of these entities will become part of your application's class structures?

### Conceptual Modeling

Describing the semantics of systems at a high level of abstraction

Specifically, conceptual modelers:

- Describe **structure models** in terms of entities, relationships, and constraints
- Describe **behavior or functional** models in terms of states, transitions among states, and actions performed in states and transitions
- Descrbie **interactions and user interfaces** in terms of messages sent and received and information exchanged

Conceptual-model diagrams are high-level abstractions that enable clients and analysts to understand one another, enable analysts and architects to communicate successfully with application programmers, and potentially generate (parts of) the software application.

### Conceptual Modeling Approaches

In additional to UML, pattern-driven design, and CVA analysis, other approaches include:

- Robustness diagrams
    - Based on analysis of use cases to confirm robustness of the use requirements of the system
    - Analyze the steps of use cases to ensure consistency with other use cases in your overall model
    - Add actors, boundary elements for major UI elements (screens, reports; only talk to controllers and actors), entities for business concepts/support (only talk to controllers), controllers for process management (can talk to controllers, boundary, and entity objects, not actors) and optionally use case references to bridge activities on diagrams
    - MVC entities fall nicely into robustness diagrams
- Object role model (ORM) diagrams and alternatives
    - A powerful method for designing and querying database models at the conceptual level, where the application is described in terms easily understood by non-technical users
    - In practice, ORM data models often capture more business rules and are easier to validate and evolve than data models in other approaces
    - Can get complex quickly
- Class responsibility collaborator (CRC) models
    - Good way to work with non-technical people to capture how a system works
    - Initially a teaching concept, became a modeling approach
    - Classes are objects, people, places, things
    - Responsibilities are anything a class knows or does
    - Collaborators are anything you need to interact with to perform a responsibility
    - Evolves into a UML class diagram
- Logical data models (LDMs) and alternatives
    - Data focused model to describe data in detail without specifics of implementation in a database
    - Used after conceptual processes have been identified 
    - Includes all entities and relationships, with attributes and keys identified
    - Database normalization can be applied to these models
    - Typically, specificy primary key for all entities, find the relationships between the different entities, find all attributes for each entity, resolve many-to-many relationships, and normalization
    - Alternatives include entity-relationship data (ER) modeling and dimensional data models
- Analysis process patterns for how we build software
    - A process pattern is a pattern which describes a proven, successfull approach and/or series of actions for developing software. At least three types: task process patterns, stage process patterns, phase process patterns
- Analysis matrix
    - Designed to help designers deal with large amounts of variations in a problem domain
    - For example, if different rules become active depending on variation in the requests involved
    - A concept becomes a row header, a variation is an entry in the matrix, related variations go into a column, and the column header groups the variations by a particular scenario relevant to the problem domain
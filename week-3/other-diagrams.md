# Other Diagrams

## Sequence Diagrams

Sequence diagrams show dynamic interactions between objects--not only how they communicate, but in what order over time

Somewhat labor intensive

Often needed to understand or clarify embedded or API-based object interactions that have timing or sequential dependencies

- Objects are show across top of diagram
    - Objects at top existed when the scenario begins
    - Other objects may be created during the sequence progression

- Each object has a vertical dashed line known as its lifeline
- When an object is active, the lifeline has a rectangle placed above its lifeline
    - If an object is released during the scenario, its lifeline terminates with an "x"

- Messages between objects are shown with lines pointing at the object receiving the message
    - The message line is labeled with the method being called and (optionally) its parameters

- All UML diagrams can be annotated with notes as needed to label or discuss operations
- Off normal sequences are usually labeled and shown separately after the complete normal sequence is demonstrated

## Activity and State Diagrams

Activity and state diagrams represent alternate ways to record/capture design information flow in your system

They can help you identify new classes and methods

They are typically used after use case creation; for instance, create an activity diagram for a given use case scenario

For each activity diagram, you might follow on and draw a sequence diagram
    - Add a class for each object in the sequence diagrams to your class diagram, add methods in sequence diagrams to relevant classes
    - Remember: sequence diagrams may not be needed for simple logic

### Activity Diagrams

Think of activity diagrams as "super flow charts"

Able to model complex, parallel processes with multiiple ending conditions

They can be partitioned to identify separate workflow activities

Easy to identify start and end points, as well as conditional selections

- Initial node (circle)/final node (circle in circle)/early termination node(circle with x)
- Activity: rounded rectangle indicates an action of some sort either by a system or a user
- Flow: directed lines between activities and/or other constructs
    - Flow can be annotated with guards that restrict its use
- Fork/join: black bars that indicate activities that happen in parallel
- Decision/merge: diamonds used to indicate conditonal logic

### State Diagrams

Shows the major states of an object or system
    - Partitions an object's behavior into various categories (initializing, acquiring info, performing calculations, etc.)
    - Documents the states and transitions between them (transitions typically map to method calls)

Often used to develop embedded device state machines

- Each state appears as a rounded rectangle
- Arrows indicate state transitions
- Each transition has a name that indicates what triggers the transition (often a method name)
- Each transition may optionally have a guard that indicates a condition that must be true before the transition can be followed
- Has a start state and an end state

## Other Useful UML Diagrams

- Communication and Interaction diagrams can be a simpler substitute for sequence diagrams to document data flow in a system
- Component-based architectures, such as microservices, may be represented using Component diagrams
- If documenting physical architecture, Deployment diagrams may be useful

Once you have written base requirements and use cases to fulfill them, and you've reviewed the use cases with clients to validate tasks and priorities, and to determine the various alternate paths, you're ready to start creating a design: class diagrams, activity diagrams, state diagrams, and sequence diagrams using information in the use cases and requirements as inspiration
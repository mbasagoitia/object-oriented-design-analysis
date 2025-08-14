# UML for OOAD: Class Diagrams

Unified Modeling Language

- Defines a standard set of notations for use in modeling object-oriented systems

We will encounter UML in the form of:

- Class diagrams
- Sequence diagrams
- State diagrams
- Activity diagrams
- Use case diagrams and more

## Object Collaboration

In response to a message, an object may:

- Update its internal state
- Return a value from its internal state
- Perform a calculation based on its state and return the calculated value
- Create a new object or set of objects
- Delegate part or all of the task to some other object
- Any behavior set by the designer

As a result, objects can be viewed as members of multiple object networks

Object networks are also called collaborations. Objects in a collaboration work together to perform tasks for their host application.

## Object Diagram Notation

- Objects are drawn as rectangles with their names and types (class names)
    - Marika:Person
- The name of the object is optional, the type is required (and so is the colon)
    - :Person
- Objects that work together have lines drawn between them. This connection has many names:
    - Object reference
    - Reference
    - Link
- Messages are sent across links
    - Links are instances of assocations

## Classes and Static

Classes can define class-based (static) attributes and methods.

- A static attribute is shared among all of a class's objects
- All objects of that class can read/write the static attribute
- A static method is a method defined on the class itself
- The method does not have to be accessed via an object; you can invoke static methods directly on the class itself
    - Example: Java's String.format()

## UML Class Diagrams

Classes in UML appear as rectangles with multiplie sections
- The first section contains its name (defines a type)
- The second section contains the class attributes
- The third section contains the class methods

- High-level conceptual class diagrams may just show the type name

## Accessibility in UML Diagrams

- You can use UML to notate which accessibility you want each member to have
    - Public: notated with +
    - Protected: notated with #
    - Private: notated with -

## Diagramming Relationships for Classes

Classes can be related in a variety of ways:

- Inheritance
- Association
- Multiplicity
- Whole-part/Grouping (Aggregation and Composition)
- Qualification
- Interfaces

Inheritance: 
    - One class can extend/inherit from another
    - UML notation: a white triangle points to the superclass
    - The subclass can add attributes
    - The subclass can add behaviors or override existing ones

## Encapsulation

Say we have an Airplane object and a Jet object that inherits from it. Here, the "speed" instance variable is private in Airplane. That means Jet does not have direct access to it. Jet must use super to access it via Airplane.

Airplane:

public void setSpeed(int speed) {
    this.speed = speed;
}

Jet:

public void setSpeed(int speed) {
    super.setSpeed(speed * MULTIPLIER)
}

## Association Relationships

One class can reference another (association)
    - Notation is a straight line

Example: viewController and View--viewController has a reference to a View object, and a View has a reference to a viewController object

- Roles can be assigned to the classes that take part in an association
    Example: A simplified model of a lawsuit might have a lawsuit object that has relationships to two people, one person with the role of the defendant and one person with the role of the plaintiff. Typically, this is implemented via "plaintiff" and "defendant" instance variables or attributes inside of the Lawsuit class.

- Associations can also be labelled in order to convey semantic meaning to the readers of the UML diagram

- In addition, associations can have multiplicity annotations, which indicate how many instances of a class participate in an association

- Classes can show assocation with themselves

## Relationships: Whole-part, Groups (Aggregation and Composition)

Associations can also convey semantic information about themselves

- Aggregations indicate that one object "contains a" set of other objects
    - A whole-part relationship between a class representing a group of components and a class representing the components (such as crate and bottles; note that the crate can exist without the bottle(s))
    - Aggregation relationships are transitive and asymmetric
    - Notation: aggregation is indicated with a white diamond attached to the class playing the container role
    - A variant of aggregation is composition, which adds the property of existence dependency
        - If A composes B, then if A is deleted, B is deleted
        - Example: I can't create a book that doesn't have a section, and I can't create a section that doesn't have a chapter
    - Notation: Composition relationships are shown with a black diamond attached to the composing class

## Qualification

An association can be qualified with information that indicates how objects on the other end of the association are found

- This allows the designer to indicate that the association requires a query mechanism of some sort
    - Example: An association between a phonebook and its entries might be qualified with a name
- Notation: A qualification is indicated with a rectangle attached to the end of an association indicating the attributes used in the query

## Abstract Classes and Interfaces

- Abstract classes are treated much the same as classes, with an annotation that they are abstract
- A class can indicate that it implements an interface
- An interface is a type of class definition in which usually only method signatures are defined
- A class implementing an interface provides method bodies for each defined method signature in that interface
- This allows a class to play different roles, with each role providing a different set of services
- These roles are then independent of the class's inheritance relationships

Other classes can access a class via its interface. This is indicated via a "ball and socket" notation or a class box labelled as an interface
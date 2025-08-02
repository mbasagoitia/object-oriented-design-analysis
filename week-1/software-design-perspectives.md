# Software Design Perspectives

## How Do We Analyze Problems?

We come up with a plan--how to represent the tasks, how we find the best actions, orders of actions, and use tasks and actions to solve a problem

For computational problems, this often results in functional decomposition--breaking a problem into smaller, solvable steps. Essentially, slice up problems until they are at a level of granularity that is easy to solve in a few steps.

However, this isn't always the best solution!

### Problems with Functional Decomposition

- Creates a design centered around a **main program**. This program is in control and knows all of the details about what needs to be done and all of the details about the program's data structures

- Creates designs that **do not respond well to change requests**. These problems are not well modularized and so a change request often requires modification of the main program; a minor change in a data structure, for example, might cause impacts throughout the entire main program.

These problems in functional decomposition occur because the resulting software exhibits:

- Poor use of abstraction
- Poor encapsulation
- Poor modularity

## Simple Definitions

**Abstraction**: refers to the set of concepts that some entity provides for achieving a task or solving a problem
    - Example: the public methods of Java's String class

**Modularity**: refers to gathering elements with common responsibility and providing clear paths to interact with those elements
    - Talked about as measures of cohesion and coupling

**Encapsulation**: refers to a set of language-level mechanisms or design techniques that group and control access to implementation details of a class, module, or subsystem from other classes, modules, and subsystems
    - In most OO programming languages, classes have sets of instance variables set to "private," which ensures that other classes cannot access the value of that variable directly
    - They need to use a method in order to retrieve or update that internal variable

A lack of modularity is often the result of weak cohesion and tight coupling

**Cohesion**: Refers to how closely the operations in a routine are related. We wanted methods/modules to do one thing.

We want our code to exhibit strong cohesion:

- Methods perform one operation
- Classes achieve a fine-grain design or implementation goal
- Packages achieve a medium-grain design goal 
- Subsystems Achieve a coarse-grain design goal
- Systems achieve all design goals and meet their requirements

**Coupling**: Refers to the strength of a connection between two routines. Complements cohesion. Weak cohesion implies strong coupling and vice versa. With strong coupling, a single change in one method or data structure will cause ripple effects and unwanted side effects. 

## Object-Oriented Design Approach

Object-oriented design is centered around the concept of an object.
    - It produces systems that are networks of objects collaboration to fulfill the responsibilities/requirements of the system

Objects are conceptual units that combine both data and behavior (the features of an object)
    - The data is referred to by many names--attributes, properties, instance variables, etc.
    - The behavior of an object is defined by its set of methods
    - Methods and attributes are members of an object (or the object's class definition)

Objects inherently know what type they are
    - Its attributes allow it to keep track of the state
    - Its methods allow it to function and interact properly

## Responsibilities of an Object

It is best to think of an object as something with responsibilities.
    - As you perform analysis, you discover responsibilities that the system must fulfill
    - You will eventually find "homes" for these responsibilities in the objects you design for the system; this process can help you "discover" objects needed for the system
    - The problem domain will also provide many candidate objects to include in the system
    - This is an example from moving to a conceptual perspective to the specification and implementation perspectives

Conceptual: a set of responsibilities
Specification: a set of methods
Implementation: a set of code and data

## Conceptual Design and Abstraction

Conceptual design is an exercise in abstraction

Abstraction answers the questions:

- How will users think about using what I develop?
- What mental model do I want to provide for them? What level of detail is needed?
- What responsibilities will classes in the design have?
- What will the connections be between elements, what methods will be exposed?

**Abstraction is the most important concern in OOAD**

The choice you make in defining the abstractions of your system will live with you for a long time

Abstraction is:

- Not just encapsulation
- Not just information hiding
- Encapsulation supports abstraction, but so does conceptual generalization, the design of exposed interfaces, and assignment of class responsibilities

## Transitioning to the Object Oriented Paradigm

Rather than having a main program do everything, populate your system with objects that can do things for themselves. Give general instructions (code to interfaces) and expect other entities to know how to apply those general instructions to their specific situation. It will be easier to add special cases by adding other independent entities.
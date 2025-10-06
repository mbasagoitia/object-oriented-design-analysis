# Template Pattern

Design principle: "Don't call us; we'll call you" -> high-level components call low-level components

The template method lives in a high-level class and invokes methods that live in its subclasses. Template methods encourage clients to interact with the abstract class that defines the template methods rather than the subclasses.

Focuses on encapsulation of the steps of an algorithm.

## Encapsulation and Template

Encapsulation is, in part, a grouping mechanism.

The main focus of encapsulation should be thought of as "any kind of hiding," especially the hiding of things that can change.

We can hide data, but also:

- Methods
- Objects
- Type
- Behavior
- Implementations
- Design details
- Derived classes
- Instantiation rules
- etc.

Templates encapsulate algorithm implementations, defining the steps of an algorithm in methods, and controlling how subclasses implement methods.

This pattern is almost more of a reminder on best practices in defining methods and designing inheritance hierarchies.

- Final methods: I want all subclasses to do this default implementation
- Abstract methods: I want all subclasses to decide on an implementation
- Hook methods: I'll give the subclass a default implementation (or no action), but the subclass can change it as needed
- "Template" methods: A process method all subclasses should make available
- Static methods: What do we want available from the class instead of from object instances--might be used to track a count of number of times the class is instantiated

Template provides:

- A reminder of the way code reuse is provided in inheritance hierarchies
- Encapsulation of elements we don't want our subclasses to change
- A tool for doing effective design by contract for an inheritance hierarchy design

## Final

When we create something we don't want to be changed in design, we could just state that by convention, this thing should be used as is--or we can finalize a definition.

In Java, we use the **final** keyword

It can be used in a variable definition to create a constant, with a method to prevent method overrides, or with a class to prevent inheritance.

## Template Pattern Defined

The Template pattern defines the skeleton of an algorithm in a method, deferring some steps to subclasses.

Template lets subclasses redefine selected steps of an algorithm without changing the algorithm's structure.

Template defines the steps of an algorithm and controls how subclasses provide the implementation for steps.

- Makes the algorithm abstract
- Each step of the algorithm is represented by a method
- Encapsulates the details of most steps
- Steps (methods) handled by subclasses are declared abstract
- Shared steps (concrete methods) are placed in the same class that has the template method, allowing for code reuse among the various subclasses


We can polymorphically call template methods, such as dailyRoutine() with our worker objects, without knowing the object instance details.
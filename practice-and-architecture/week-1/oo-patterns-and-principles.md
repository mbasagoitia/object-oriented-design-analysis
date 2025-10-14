## OO Patterns and Principles

SOLID is an important set of principles, but far from complete. There are also other principles that can provide more guidance for robust OO solutions.

General:

- Program to interfaces, not implementations
    - Let polymorphism be your friend; if you have a choice, code to an abstract base class or interface instead of an implementation or subclass details
- Encapsulate what varies
    - Identify the ways in which your software will change
    - Hide the details of what can change behind the public interface of a class
- A class should only have one reason to change
    - Each class should have only one design-related reason that can cause it to change
- Classes are about behavior, not specialization
    - Emphasize the behavior of classes over the data of classes
    - Do not subclass for data-related reasons
- Favor delegation (composition) over inheritance
- Strive for loosely coupled designs between objects that interact
- Only talk to your (immediate) friends
- Don't call us, we'll call you

SOLID:

- Single responsibility principle
    - Every object in the system should have a single responsibility, and all of the object's services should be focused on carrying it out
- Open/closed principle (classes should be open to extension but closed for modification)
- Liskov substitution principle
    - Subtypes must be substitutable for their base types
- Interface segregation principle
    - Define subsets of functionality as interfaces
- Dependency inversion principle (depend on abstractions, not concrete classes)

Other:

- Don't repeat yourself (DRY)
- You aren't going to need it (YAGNI)
    - When developing code, avoid "presumptive" features--there are clear costs associated with writing code before it is needed
- The principle of healthy skepticism
    - Don't depend on patterns for everything; they are useful guidelines, but dangerous crutches

Analyzing cohesion in a system: example

For each class C and method M, write "the C Ms itself"--the automobile drives itself, the automobile starts itself

If any one of the generated sentences does not make sense, investigate further--"the automobile puts fuel in itself"

You may have discovered that a service should belong to a different responsibility of the system and should be moved to a different class (such as gas station).

Open-closed principle:

- Prevent or heavily discourage changes to the behavior of existing classes, especially those near the root of an inheritance hierarchy.

- If a change is required, one approach would be to create a subclass and allow it to extend/override the original behavior. This means you must carefully design what methods are made public and protected in these classes.

- Inheritance is certainly one way to apply this principle, but composition and delegation offer more flexibility.

Liskov Substitution principle:

- Instances of subclasses do not violate the behaviors exhibited by instances of their superclasses. They may constrain that behavior, but they do not contradict it.

Interface segregation principle:

- No client should be forced to depend on methods it doesn't use

- The goal is to reduce the impact and frequency of changes by splitting software into multiple, independent parts

- Correct abstraction is a key to this--keeping interfaces small and cohesive. Also need the ability to inherit multiple interfaces if required

Reasons to create a class:

- Model a real-world object
- Model an abstract object
- Reduce complexity
- Isolate complexity
- Hide implementation details
- Limit the impact of change
- Hide global data
- Streamline parameter passing
- Make central points of control
- Facilitate reusable code
- Plan for a family of programs
- Package related operations
- Accomplish specific refactoring

Classes to avoid:

- "God" classes
- Irrelevant classes
- Classes that are verbs (behavior only)
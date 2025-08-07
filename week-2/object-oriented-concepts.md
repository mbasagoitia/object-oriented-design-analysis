# Object-Oriented Concepts

## Classes and Objects

Objects are instances of a class

Classes define the complete behavior of their associated objects, such as what data elements and methods they have and how these features are accessed (public/private etc.)

A class defines a type with a legal set of values. Subclasses can be defined that exclude some elements of the superclass

## Class Inheritance

Classes can exhibit inheritance relationships

- Behaviors and data associated with a superclass are passed down to instances of a subclass
- The subclass can add new behaviors and new data that are specific to it; it can also alter behaviors that are inherited from the superclass to take into account its own specific situation, making it a derived class
- Ideally, any property that is true of a superclass is true of a subclass; the reverse is not true; it is ok for properties that are true of a subclass to not be true of values in the superclass

- Inheritance relationships are known as "is-a" relationships--undergraduate is-a student; a subclass of student
- A subclass represents a more refined, more specific version of the superclass
- Our goal is to treat the subclass as if it is the superclass--this allows code that was built to process the superclass to equally apply to the subclass

## Class Encapsulation

- Classes can control the accessibility of the features of their objects. They can typically specify whether an attribute or method has an accessibility of public, protected, or private
- This ability to hide features of a class/module is a key part of encapsulation/information hiding
- Encapsulation is more than just hiding data (will be discussed later)

- **Public** visibility of a feature -> all objects can access it
- **Protected** -> instances of the class and its subclasses can access it; access only within inheritance hierarchy
- **Private** -> only instances of the class itself can access it

The above are only general definitions, and different programming languages implement these accessibility modifiers in different ways.

## Class Constructors/Destructors

Classes can control how their objects are created and destroyed

- Object-oriented languages will often provide special methods known as constructors and destructors/finalizers to handle these two phases in an object's lifecycle
- Constructors ensure that an object is properly initialized before any other object makes use of it. A class may have multiple constructors
- Destructors ensure that an object has released all of the resources it consumed while it was active

Some languages, including Java, have garbage collection--if you're not using an object anymore, eventually that inactive object's memory will be reclaimed and reused--but we don't know exactly when that will happen. Using a destructor lets us tell the object exactly when it is inactive.

## Superclasses

A well-defined class structure lets us treat all instances of a superclass-subclass hierarchy as if they are all instances of the superclass, even if some are instances of subclasses.

## Polymorphism

"Many forms"

Polymorphism lets us treat objects as if they are instances of an abstract class but get the behavior that is required for their specific subclass.

Being able to refer to the different derivations of a class in the same way, but getting the behavior appropriate to the derived class being referred to.

In practice, this allows code to be written with respect to the root of the inheritance hierarchy and function correctly when applied to the hierarchy subclasses

With polymorphism, a message ostensibly sent to a superclass may be handled by a subclass. Most specific method definition will be applied.

## Abstract Classes

The classes that sit at the top of an object hierarchy are often defined as abstract classes, while the classes that sit near the bottom of the hierarchy we create instances of are called concrete classes.

- Abstract classes define the generic behaviors and data for a related set of subclasses
- They act as placeholders for other classes defining method signatures that they must implement, defining method bodies for behaviors that should be the same across all subclasses, defining data that will be useful for all subclasses
- In OO programming languages, abstract classes cannot be instantiated. Instead, you instantiate concrete subclasses but access them via the interface defined by the abstract class

## Delegation

Principle: **Favor delegation over inheritance**

When designing a class, there are four ways to handle an incoming message:

- Handle message by implementing code in a method
- Let the class's superclass handle the request via inheritance
- Pass the request to another object (delegation)
- Some combination of the previous three

Delegation is employed when some other class already exists to handle a request that might be made on the class being designed. The host class simply creates a private instance of the helper class and sends a message to it when appropriate. As such, delegation is often referred to as a "Has A" relationship--i.e., a car HAS-A engine object.

Example: Delegate functionality to a GroceryList abstraction that handles adding and removing items "under the hood" via a LinkedList class that implements the List interface. This way, an outside client knows exactly what the GroceryList class is supposed to do.

- It will still "work" if we directly use LinkedList, but the abstraction is not as clear. It makes it easier to for clients to use a well-defined abstraction.

- We can also change delegation relationships at runtime, unlike inheritance relationships

- Not a good idea to inherit directly from LinkedList

Delegation uses **associations** between classes--the ability to refer to an instance of an object from another class to use it for its own responsibility

**Aggregation** is having associations with groups of objects

**Composition** is requiring those associations with a group of objects to exist
    - Existence dependency: groups of objects must all exist to have a functional design

## When to Use Inheritance

Inheritance is a mechanism for sharing (public/protected) features between classes. Should clearly fall into the "is-a" relationship.

Avoid implementation inheritance--do not use inheritance to implement some functionality!

An important aspect of inheritance is substitutability
    - Since a subclass exhibits all of the behavior of its superclass, it can be used anywhere an instance of its superclass is used
    - This behavior is polymorphism

Furthermore, subclasses can add additional behaviors that make sense for them and can override behaviors provided by the superclass, altering them to suit its needs. This is both powerful and dangerous!

## Design by Contract

We can view a class's public methods as establishing a contract that it and its subclasses promise to keep. If we code to the root contract, we can create very robust and easy to maintain software systems. The danger comes from the possibliity that a subclass may change the behavior of a method (such as different return type or argument structure) such that it no longer follows the contract established by a superclass.

Design by contract can be implicit or explicit. There are languages and libraries to allow explicit design by contract specification.

Abstract classes and interfaces make the design by contract principle more explicit.

An abstract class cannot be directly instantiated; it is designed from the start to be subclassed. It does this by providing method signatures but not implementations for them, essentially setting the contract that each subclass must meet.

Interfaces go one step further and only allow the declaration of abstract methods. You cannot provide method implementations for any of the methods declared by an interface in the interface itself. Useful when you want to define a role in your software system that could be played by any number of classes.

## Override vs Overload

- Override: run time polymorphism
    - Normall what we mean by polymorphic methods
    - The superclass has a method with a certain signature
    - The subclass declares the same method and same signature, but with different behavior

- Overload: compile time polymorphism
    - The class in question may have two methods of the same name with different signatures and different behavior
    - Common for constructors
    - We can call whichever version  by providing the appropriate arguments

## Generic Components

In most object-oriented languages, we have the concept of generic components: elements with an interface and related semantics of the data structure that are independent of its contents.

Generics allow us to abstractly define classes and methods that can functionally be used with a variety of other objects

## Object Identity

In OO programming languages, all objects have a unique id, perhaps its memory location or a unique value assigned to it when it was created.

This id is used to enable a comparison of two variables to see if they point at the same object.

Identity complicates the concept of equality for objects...

In Java, == checks whether something is the same object, and equals() checks whether two objects have the same contents

## Identity in OOAD

Identity is also important in analysis and design

We do not want to create a class for ojects that do not have a unique identity in our problem domain
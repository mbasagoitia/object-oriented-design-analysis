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

Being able to refer to the different derivations of a class in the same way, but getting the behavior appropriate to the derived class being referred to

## Abstract Classes

The classes that sit at the top of an object hierarchy are often defined as abstract classes, while the classes that sit near the bottom of the hierarchy we create instances of are called concrete classes.

- Abstract classes define the generic behaviors and data for a related set of subclasses
- They act as placeholders for other classes defining method signatures that they must implement, defining method bodies for behaviors that should be the same across all subclasses, defining data that will be useful for all subclasses
- In OO programming languages, abstract classes cannot be instantiated. Instead, you instantiate concrete subclasses but access them via the interface defined by the abstract class
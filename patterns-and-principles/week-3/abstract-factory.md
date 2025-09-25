# Abstract Factory

Abstract factory takes the factory concept further by providing a way to instantiate "kits" or sets of objects needed to produce a complex product.

## Using Factories in OO Design

It is important to manage the creation of objects.

- Code that mixes object creation with the use of objects can quickly become non-cohesive
- A system may have to deal with a variety of different contexts, with each context requiring a different set of objects
- In design patterns, the context determines which concrete implementations need to be present

The code to determine the current context, and thus which objects to instantiate, can become complex with many different conditional statements.

With factory, the conditional code for selection goes inside the factory and we pass in parameters associated with the current context, getting back the objects you need for the situation, then using those objects to get your work done

Factories concern themselves just with creation, letting your other code focus on other functionality, providing higher cohesion.

### One Rule One Place

An object should either create/manage a set of objects OR it should use other objects, never both. Look for ways to separate out the creation of objects from the code that makes use of those objects. Encapsulate the creation process and you can change it as needed without impacting the code that uses those objects. Again, this rule is a guideline. 

The client should interact with an interface or abstract class, not concrete implementations of classes, and the factory knows nothing about how to use the abstract interface; it just creates the objects that implement it.

Using factories limits the impact of change. If a change request relates to the creation of an object, the change will likely occur in a factory--all client code will remain unaffected. If a change request does not relate to the creation of objects, the change will likely occur in the use of an object or the features it provides.

## Abstract Factory

The abstract factory design pattern provides an interface for creating families ("kits") of related or dependent objects without specifying their concrete classes.

Abstract factory is about making objects that are built up of other objects (object composition).

The component (such as table) factory abstract class has a kitName that says what the kit is, and each component factories that we make returns a surface, wood parts, and hardware that gives us the kit of things that we need

Each component factory will have "kits" of objects made from concrete instances of the abstract classes

The concrete ClassicTableComponentFactory subclass knows which concrete components are used to make up the kit for a Classic Table.

- Create an interface for each distinct product, and each product's variants will inherit from it
- Inside the abstract creator class (such as company, store, etc.), include a list of abstract creator methods for each abstract product
- Clients work with any concrete factory
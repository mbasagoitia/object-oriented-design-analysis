# Creational Patterns and Factory

Creational patterns focus on different approaches to instantiating objects and help to decouple the creation of objects from their use.

Standard creational patterns include:

- Factory
- Abstract Factory
- Singleton
- Prototype
- Builder

## Factory and the Problem with New

When we use "new" in our code to instantiate an object, we're breaking encapsulation of type.

Needs to be recompiled each time a dependency changes

Our goal is to have code that instantiates subtypes without having complex conditionals, recompiling, and that makes it easier to add/remove subclasses.

Sometimes, our code may contain both the creation and preparation (use) steps.

Example:

class TableStore {
    Table makeTable(String type) {
        Table table;
        // creation steps
        if (type.equals("Coffee")) {
            table = new CoffeeTable();
        } else if (type.equals("Game")) {
            table = new GameTable();
        } else if (type.equals("Card)) {
            table = new CardTable();
        }
        // preparation steps
        table.cut();
        table.finish();
        table.testFit();
        table.box();
        return table;
    }
}

This code mixes creation and preparation--this may work in some cases, especially if you expect few changes.

However, we can improve it by encapsulating creational code.

We will encapsulate it and put it in a different class. That new class depends on the concrete classes, but those dependencies no longer impact the preparation code.

### Simple Factory

We will move the creational code into its own class for reference by code where the objects are needed.

class TableStore {
    private SimpleTableFactory factory;
    public TableStore(SimpleTableFactory factory) {
        this.factory = factory;
    }
    
    public Table orderTable(String type) {
        Table table = factory.makeTable(type);
                // preparation steps
        table.cut();
        table.finish();
        table.testFit();
        table.box();
        return table;
    }
}

The SimpleTableFactory will now run the conditional statement to return the requested table type.

Still some issues here; need to know the available types. Should the type argument be a String or an enum?

## Factory Method

In the simple factory table approach, the concrete products like GameTable extend the abstract table class to get the factory method that table has a reference to.

When we say the concrete product implements an interface, it doesn't mean a class that implements a Java interface using the implements keyword.

Implements an interface means that the concrete class is implementing a method from the supertype (which could be a class or interface)

The factory method design pattern allows you to:

- place abstract "code to an interface" code in a superclass
- place object creation code in a superclass
- TableStore becomes an abstract class (or interface) with an abstract createTable() method
- create subclasses that can override elements of createTable() for each style at each table store type

Example:

Stores use createTable to specify which table object to make when a type of table is requested in an order

Table concrete classes can specialize the standard elements of the makeTable process

Pass a type (classic, modern, etc.) to the abstract Table class, and then a concrete implementation of a specific type of store handles the logic for determining what variant of table within that type to create.

The framework provides a createTable method for each store type to provide concrete table objects. The framework then calls makeTable assuming that the concrete table object has the standard steps for the defined process. Each concrete store will create custom concrete table objects that can vary elements as needed.

Creator (Store) and Product (Table) are both abstract classes. ConcreteCreator (ModernStore) makes concrete products of a certain concrete type (ModernCoffeeTable)

### Factory Pattern Specifics

- Product declares an interface which is common to all objects that can be produced by the creator and its subclasses
- Concrete products are different implementations of the product interface
- Creator declares the factory method that returns product objects
- It could be an abstract method, making concrete creators implement local versions, or it could have a base variation that returns a default product type
- Concrete creators override the factory method to return different product types
- The "created" products could come from a cache, an object pool, or some other source, it doesn't have to be new instances
- Creators and Products could be based on abstract classes or interfaces

### Factory and the Dependency Inversion Principle

Factory is one way of following the dependency inversion principle: "depend upon abstractions, not concrete classes." We don't want the client to depend on concrete implementations.

- Variables should not hold references to concrete classes
- No class should derive from a concrete class, only interfaces or abstract classes
- No method should override an implemented method of base classes; override abstract methods. If it's implemented in the base class, it's meant to be used by subclasses

Remember that these are guidelines, not rules

## Summary

Factory is useful when a class will benefit from abstracting or delegating responsibility for creating objects to helpers.

Using factory increases the flexibility of creating objects and possible extended versions of those objects, without impacting other application logic.

Factory is useful for parallel class hierarchies where a subject concrete class wants to refer to a parallel delegated concrete helper class. 

Factories are creating objects via inheritance.
# Dependency Injection

Dependency injection is a technique for assembling applications at runtime from a set of concrete classes that implement generic interfaces without the concrete classes knowing about each other. 

This allows you to create loosely coupled systems as the code you write only ever references the generic interfaces that hide the concrete classes.

Think about a "needs-a" relationship for dependency injection. The idea is that classes indicate their dependencies in abstract ways, and then a third party injects a class that will meet that dependency at runtime. The third party is known as an assembler and comes from an IoC (inversion of control) container or a dependency injection framework.

## Inversion of Control

A principle in software engineering by which the control of objects or portions of a program is transferred to a container or framework--any time the main control of the program was "inverted" away from your code to the framework code.

Example: instead of UIs being controlled by the application program, the UI framework would contain the interactions and your program instead would provide event handlers for the various fields on the screen.

The term dependency injection describes an approach that a container uses to ensure that any user of a plugin follows some convention that allows a separate assembler module to inject the implementation into the lister.

Dependency injection is a pattern which implements inversion of control, where the control being inverted is the setting of object dependencies.

The act of connecting objects with other objects, or "injecting" objects into other objects, is done by an assembler rather than by the objects themselves.

As much as possible, we want to get rid of code with the form Foo f = new ConcreteFoo(); we want to invert the control to something else.

## Types of Dependency Injection

- Constructor Injection: the class indicates its dependency via its constructor, such as:
    - public MovieLister(MovieFinder finder) {
        this.finder = finder;
    }
    - This essentially says "I need a MovieFinder"

- Setter Injection: the class indicates its dependency via a setter
    - public void setMovieLister(MovieLister lister) {
        this.lister = lister;
    }

- Field injection: an individual attribute is injected into a component

- Interface injection: an interface provides an injector method to inject dependencies into passed clients

## Basic Idea

Take a set of components (concrete classes and interfaces), add a set of configuration and metadata ("when you run this code, use this code for that run") and provide that to a dependency injection framework that knows how to bring those things into the code via some metadata. Finish with a small set of bootstrap code that gets access to an IoC container, retrieves the first object from that container by supplying the name of a generic interface, and invokes a method to kick things off.

## Dependency Injection Frameworks

Give us the ability to remove the names of concrete classes out of our source code while having those classes automatically instantiated and injected into your system based on configuration metadata.

Frameworks include Spring, Guice, Dagger

## Why Use DI?

One typical example is testing, where you might want to inject test code for select unit tests.
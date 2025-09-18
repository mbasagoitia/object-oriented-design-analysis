# Facade

Key structural OO design pattern

Provides a unified interface to a set of interfaces in a subsystem. Facade defines a higher-level interface that makes the subsystem easier to use.

There can be significant benefit in wrapping a complex subsystem with a simplified interface. If you don't need the advanced functionality or fine-grained control of the whole subsystem, the simpler interface makes life easier.

Facade works best when you are accessing a subset of the subsystem's functionality. You can also add new features by adding it to the facade (not the subsystem) and still get a simpler interface.

Facade not only reduces the number of methods you are dealing with but also the number of classes. Client code is simplified and dependencies are reduced; all steps for high-level services that we expose to the client are encapsulated in the facade.

A facade not only simplifies an interface; it decouples a client from a subsystem of components.

# Adapter

The adapter pattern provides steps for converting an incompatible interface with an existing system into a different interface that is compatible.

The adapter pattern converts the interface of a class into another interface that clients expect. It lets classes work together that couldn't otherwise because of incompatible interfaces.

- The client makes a request on the adapter by invoking a method from the target interface on it
- The adapter translates the request into one or more calls on the adaptee using the adaptee interface
- The client receives the results of the call and never konws there is an adapter doing the translation

The adapter has a reference to the adaptee and invokes its specific method

## Adapter Alternate Structure

A class adapter (as opposed to an object adapter, above) requires use of multiple inheritance--but now, adapter does not need to re-implement target and/or adaptee behavior. It simply overrides or inherits that  behavior instead.

## Comparing Facade and Adapter

Both patterns act as wrappers of a preexisting class, and both take an interface that we don't want and convert it to an interface that we can use.

With facade, the intent is to **simplify** the existing interface.

With adapter, we have a target interface that we **convert**. In addition, we often want the adapter to plug into an existing framework and behave polymorphically.
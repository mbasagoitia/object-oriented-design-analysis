# Structural Patterns

Structural patterns help in composition of classes or objects into larger or more complex structures, but maintain efficiency and flexibility.

Structural design patterns include:

- Decorator
- Facade
- Adapter
- Proxy
- Composite
- Flyweight
- Bridge

# Decorator

Provides a powerful mechanism for adding new behaviors to an object at runtime without requiring modification to the class. The mechanism is based on the notion of "wrapping" (delegation), but with the added element that both the delegator and the delegate implement the same interface.

This supports the goal of the open-closed principle: classes should be open for extension but closed to modification. Inheritance is one way to do this, but composition and delegation are more flexible (and Decorator takes advantage of delegation).

- Start with object A that implements interface C
- Create object B that also implements interface C
- Pass A into B's constructor and then pass B to A's client
- The client thinks it is talking to A (via C's interface) but it is actually talking to B
- B's methods augment A's methods to provide new behaviors

Decorators create chains of objects that start with the added decorators and end with the concrete components

Decorator is a subclass of whatever it is that you're decorating. The decorator itself has a reference to what it is decorating.

Essentially, decorators are wrapped around the component and the client thinks it is talking to the component
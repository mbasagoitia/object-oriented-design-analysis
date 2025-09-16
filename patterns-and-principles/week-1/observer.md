# Observer Pattern

## Types of Patterns

Some books suggest that OO patterns can be divided into creational, behavioral, and structural patterns

- Creational patterns: focus on instantiating objects and decoupling creation of objects from their use
- Behavioral patterns: look at the interactions and responsibilities of interacting objects and classes
- Structural patterns: help in composition of classes or objects into larger or more complex structures

Patterns by type:

- Behavioral: Strategy, Observer, Command, State, Template, Iterator, Mediator, Memento, Interpreter, Chain of Responsibility, Visitor
- Creational: Factory, Abstract Factory, Singleton, Prototype, Builder
- Structural: Decorator, Facade, Adapter, Proxy, Composite, Flyweight, Bridge

## Observer

Much of OO systems is focused on passing messages and events between interacting system elements.

The Observer pattern allows objects to keep other objects informed about events occurring within a software system (or across multiple systems)

It is dynamic in that an object can choose to receive or not receive notifications at runtime

Observer is one of the most heavily used patterns in the JDK and is present in many other frameworks and libraries  

Similar to subscribing to a newspaper:

- A newspaper comes into existence and starts publishing editions
- You become interested in the newspaper and subscribe to it
- Any time an edition becomes available, you are notified (by the fact that it is delivered to you)
- When you don't want the newspaper anymore, you unsubscribe
- The newspaper's current set of subscribers can change at any time

Observer is similar to this, but we call the publisher the "subject" and we refer to subscribers as "observers"

Observer can also be considered a broadcaster, since the publisher is sending messages out regardless of who subscribes 

## Observer Interactions

- The subject has a list of observers
- If the subject has a data change/event, it notifies the observers in its list
- An observer can then decide to ask the subject for updated data if needed
- Observers can join or leave the subject's list of observers at any point

The Observer pattern defines a one-to-many dependency between a set of objects, such that when one object (the subject) changes, all of its dependents (observers) are notified and updated automatically

Subject interface:

- registerObserver()
- removeObserver()
- notifyObservers()

Observer interface:

- update()

When the update method is called on an observer, it can then getState() or setState() on the subject to get updated data

## Benefits of Using Observer

Creates a loosely-coupled interaction between subject and observer--they can interact with very little knowledge about each other

The subject only knows that observers implement the Observer interface. We can add/remove observers of any type at any time, and we never have to modify subject to add a new type of observer

We can reuse subjects and observers in other contexts

Observers may have to know about the ConcreteSubject class if it provides many different state-related methods

Otherwise, data can be passed to observers via the update() method

## Concerns for Observers

Need to maintain clarity in the design about why notifications will happen. Knowing why notices occur will help in design of observer logic

Dealing with unexpected updates; observers and observed objects have no knowledge of each other's state or existence. A simple subect change may cause updates to observers and all dependent objects. When dependency criteria is not well-defined or maintained, unexpected updates can cause issues which may be hard to track down.

Overly-simple connectivity? In the base form of the simple update protocol, no details are provided on what changed in update call from the subject. Without additional protocol details to help observers, they may be forced to work to discover what the subect changes are.

Push or pull? Having the observers query the subject for what changed is a "pull" model. Including detailed information about changes in notifications would be a "push" model.

## Variations/Issues

- Push vs pull
- Event objects--strings, class/subclass, data types, generics
- Who manages subscriptions--the publisher, a broker, a separate subscription manager
- Who issues events--direct from publishers, via brokers
- Subscribers' capability to ignore events
- Complex flows--queued events, prioritized events, addressed events
- Publisher and observer in one--local event flows
- Deleting subjects or observers--notifications, error conditions

## Observers in Java

- Make your own--easy to code up
- java.beans PropertyChangeListener interface and PropertyChangeSupport; Flow class from java.util.concurrent with four interfaces (Flow.Publisher, Flow.Subscriber, Flow.Processor, Flow.Subscription)
- Other pub/sub models: could use an MQTT broker with Java from a standard message queuing app like RabbitMQ or a pub/sub socket connection using a library like ZeroMQ
# Strategy Pattern

Used for assigning behavior from families of related algorithms

## Different Approaches to Reuse

Inheritance gives us:

- Good: code reuse
- Bad: Common behaviors in root classes decay as subclasses are added

Interfaces give us:

- Good: specificity--only subclasses that need methods get them
- Bad: duplicating code for implementations in subclasses

Abstract base class:

- Could implement interfaces instead as abstract base classes and then inherit from them into subclasses, but the language would need to support multiple inheritance

## Key Object-Oriented Principles

- Encapsulate what varies
- Favor composition/delegation over inheritance
- Program to interfaces, not implementations
- Strive for loosely-coupled designs between objects that interact
- Classes should be open for extension, but closed for modification
- Depend on abstractions, not concrete classes
- Only talk to your friends
- Don't call us, we'll call you
- A class should have only one reason to change

Encapsulate what varies--for the duck problem, the "what varies" is the behaviors between Duck subclasses. We need to pull out behaviors that vary across subclasses and put them in their own classes (encapsulate them)

The result: fewer unintended consequences from code changes and more flexible code

Rather than the Duck class having fly() and makeNoise() methods directly, create two sets of classes, FlightBehavior() and NoiseBehavior(). We make sure that each member of the two sets implements a particular interface.

Other classes can gain access to these behaviors and we can add additional behaviors without impacting other classes

Important note: "code to an interface" does not imply a Java interface.

We can implement "code to an interface" by defining a Java interface and then have various classes implement that interface, or, we can "code to a supertype" and instead define an abstract base class which classes can access via inheritance

When we say "code to an interface," it implies that the object that is using the interface will have a variable whose type is the supertype, whether it is an interface or abstract base class. It can point to any implementation of that supertype and it is shielded from their specific class names.

For example, a Duck will point to a flight behavior with a variable of type FlightBehavior, NOT of type WingFlier; the code will be more loosely-coupled as a result. Abstractly reference a set of behaviors, not a specific behavior.

## Bringing it All Together: Delegation

To take advantage of these new behaviors, we must modify Duck to delegate its flight and noise behaviors to other classes, rather than implementing this behavior internally.

We will add two attributes that store the desired behavior and will rename fly() and makeNoise() to performFlight() and performNoise(). Therefore, each derived class inherits these methods and plugs in the appropriate behaviors to make sure that it does the right thing if those methods are invoked. Also add the methods setFlightBehavior() and setNoiseBehavior() that subclasses can call.

Now, when we create a Duck, it will be **composed** of the Duck and its references to the delegated behaviors.

Duck delegates to each set of behaviors and can switch among them dynamically if needed.

The behaviors can be set by the constructors of the subclasses at instantiation

The **Strategy Pattern** defines a family of algorithms, encapsulates each one, and makes them interchangeable. Strategy lets the algorithm vary independently from clients that use it.

## Applying Strategy

- Use when related classes differ only be behavior; Strategy allows configuring a class instance with a selected behavior
- Use construction or instantiation to set initial behavior
- Varies an algorithm used in a class with an outside focused hierarchy of reference algorithms
- Encapsulates data clients shouldn't know about, but the algorithm uses
    - Helps protect complex, algorithm-specific data structures
- Eliminates conditionals by composing selected Strategy algorithms at object instantiation
    - In many cases, a complex conditional statement should trigger a code smell--how else can I handle these alternatives?
- Realize that Strategy will increase the number of classes in the solution and the objects in use

## Strategy Provides Delegation

Purpose: allows an object's behavior to be customized without forcing a developer to create a subclass that overrides default behavior

Structure: Host object, delegate interface, delegate object, client

- Client invokes method on host
- Host checks to see if delegate handles this method; if so, it routes the call to the delegate, if not, it provides default behavior for the method
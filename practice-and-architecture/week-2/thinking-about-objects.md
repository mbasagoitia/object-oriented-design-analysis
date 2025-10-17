# Thinking About Objects

When we think about object design, we want to focus on the responsibilities of the object--what is it doing as it relates to other objects? What do we go to that class for?

Objects are "things with responsibilities;" we want to focus on behavior, not data. Stay at a conceptual level as long as you can before dropping down to specification and implementation.

The responsibilities come from requirements.

The process of analysis becomes:

- Find all the responsibilities of the system

The process of design becomes:

- Find a home for each responsibility (object/subsystem)

## New Perspective on Objects

A focus on responsibilities also promotes a focus on defining the public interface of an object--methods exposed and how to use them.

Hiding the implementation behind an interface decouples it from the object using that interface.

Traditionally, encapsulation implies "hiding data," but this view is too limited and focuses on the data when we want to focus on responsibility. Encapsulation helps us focus on the abstraction that we want to present to clients. What methods do we want you to think about? What do we not want you to have to think about?

We can certainly hide data, but also behavior (especially things that vary), implementations, design details, derived classes, instantiation rules, etc. and the mechanisms can involve more than just attribute and method visibility annotations--design patterns, subsystem boundaries, interfaces, etc.

Abstract types provide the means for decomposing designs aroudn the major services the system provides (encapsulation of types).

Encapsulation of type provides a new way of looking at inheritance: subclasses of the abstract types are grouped because they all behave the same way (as defined by the methods of the abstract type). This contrasts with inheritance, which is used to specialize/make more specific an existing class.

Specialization issues and considerations:

Say we create a subclass of Pentagon, SpecialBorderPentagon.

Pros:
- Reuse pentagon's behavior
- Enable variation with borders

Cons:
- Weak cohesion; if I specialize again with another border, I've got classes that all deal with both pentagons and borders
- Poor reuse; how do I share my borders with circles?
- Does not scale across multiple dimensions; SpecialBorderBlinkingSpinning Pentagon(???)

Inheritance for specialization can lead to bad designs. Instead, encapsulate variation in behavior using a pattern like Bridge or Strategy.

- Subclasses become manageable as they are partitioned across multiple abstract types (FlyBehavior)
- Lots of polymorphic behavior is enabled since classes like pentagon become customizable
- Reuse is enabled because circle can fit with these classes as well
- This approach scales; one new abstract type, one concrete subclass for each new behavior that varies

It may not always be appropriate to do inheritance when the classes behave differently (such as square inheriting from rectangle; they share some properties, but don't behave the same way like when setting width, for example. In this case, it is better to delegate some things to rectangle when the behavior is the same, and have specific square methods for when it is not).
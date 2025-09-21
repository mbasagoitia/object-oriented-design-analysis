# Flyweight and Bridge

Both have somewhat of a special or marginal use case; they aren't used as often as other patterns.

## Bridge

Used to decouple an abstraction from its implementation so that the two can vary independently

Allows a set of varying abstract objects to implement their operations in a number of ways all in a scalable fashion

Example:

We want to make different types of remote controls (different styles and behaviors) that work regardless of which device they will eventually control (tv, radio, etc.)

The question is how do we relate the remote abstraction instances to the device implementations?

We might initially use a pure inheritance approach to make specialized remotes. However, inheritance should be used for behavior, not specialization.

Using bridge, the remote control has access to (delegates to) the device interface. The relationship between the abstract class RemoteControl and the interface Device is the "bridge" between the varying abstraction and implementations. The reference to which device is being controlled by the remote when it is instantiated, setting the delegated relationship between the elements.

Remotes need to code to the interface presented by the device code.

Bridge is a structural version of Strategy; strategy is focused on behavior variations (the implementations), whereas bridge is a structural variation (both sides of the bridge).

## Flyweight

Flyweight is trying to use sharing unique data to reduce data stored with large numbers of objects that have both internal and external data.

Flyweight is suggested when a single instance of a class could represent many "virtual" instances, such as collections of objects with little variation, often small or simply defined. It can work with both defining the individual objects, the families or types of objects, and operations on the collection of all objects.

Example: Drawing application that places trees of various size at different locations on a screen. We have two types of state/data: intrinsic (color and type, defined when instantiating the class), and extrinsic that varies by individual tree (age, location, defined at runtime by method parameters).

- We keep intrinsic state (type and color) in the Flyweight class (TreeType), and use a Flyweight Factory (TreeFactory) to avoid duplicating TreeType instances.

- The ContextObject (Tree) provides for extrinsic unique tree date (age, x, y) and references one of the Flyweight types

- Forest tracks individual objects (age, x, y, and a reference to TreeType) but flyweight instrinsic data is not duplicated once defined.

Usually, the factory method getFlyweight will not create a new flyweight object if one exists that can be referenced.
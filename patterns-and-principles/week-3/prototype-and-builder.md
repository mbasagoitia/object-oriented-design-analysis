# Prototype

Used when creating an instance of a given class is either expensive or complicated. Involves cloning rather than making a new object.

Java has a Cloneable interface that lets you override the clone() method so you can tailor how copied objects should be made. Java classes that are to be cloned should implement the Cloneable interface.

Instead of calling tree = new Tree(), on the class that implements Cloneable, call tree = (Tree) super.clone()

- The client is telling the prototype to clone itself and create an object
- Prototype is an interface and declares a method for cloning itself
- ConcretePrototype implements the operation to clone themselves
- In Java, this typically means using the clone() method or some form of deserialization when you need deep copies
- A key aspect of this pattern is that the client code can make new instances without knowing which specific class is being instantiated

## Prototype Deep vs Shallow Copies

- In applying prototype, we often implement the Cloneable interface to allow Java to use the clone() method.
- But when we're trying to clone an object, we should decide between making a shallow or a deep copy, depending on requirements.
- For example, if the class contains only primitive and immutable fields, we may want to use a shallow copy (not including referred objects).
- If it contains references to mutable fields, we may want to go for a deep copy (including copies of referenced objects found in original).
- We could do this with copy constructors or serialization/deserialization approaches.

## Prototyping Considered

- Prototype doesn't require subclassing, but it does require an "initialize" operation vs. the Factory that requires subclassing but doesn't require initialization.
- Designs that make use of Composite and Decorator patterns can often benefit from Prototype.
- Prototype uses one instance of a class as a breeder of all future instances.
- Prototype is unique among the other creational patterns in that it doesn't require a class, only an object.
- Prototype hides the complexities of making new instances from the client and provides the option for the client to generate objects whose type is not known.
- Some object-oriented languages use prototypes for creating objects (JavaScript, Lua, Io, etc.).

# Builder

The Builder pattern separates the construction of a complex object from its representation so that the same construction process can create different representations.

Allows you to vary internal options for new objects, providing fine control over selections.

Use Builder when:

- Each object has selectable parts or settings that can vary as an object is constructed
- The algorithm for creating a complex object should be independent of the parts that make up the object and how they are assembled
- The construction process must allow different representations for the object being constructed

Builder helps allow choice in the creation/configuration process of complex objects. The steps may not necessarily be ordered or all be present.

- A Director interacts with a Builder to guide the creation of a Product
- The client creates the Director and a specific Builder and then asks the Director to create the Product
- The client retrieves the Product directly from the ConcreteBuilder

AlertDialog.Builder is a ConcreteBuilder used to create/configure instances of AlertDialog (the Product)

The use of linked clauses to add specific elements to the built object is typical in Builder implementations. This style is known as a fluent interface and is a best practice for API design.
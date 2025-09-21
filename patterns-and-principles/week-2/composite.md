# Composite

The single responsibility principle states that a class should only have one reason to change. Really, classes should be cohesive--supporting a single purpose.

Every responsibility we add is another area of potential change; if we have to modify code, problems may arise or propagate.

The composite pattern allows for composing objects into tree structures, treating individual and composed objects the same way. The problem is representing a part-whole hierarchy that allows uniform treatment of parts or whole object structures.

The pattern presents a solution of providing one interface for both leaf (part) and composite (whole) objects.

In use, a client creates a composite object which can have one or more child objects (either leaf or other composite objects); the composite object provides methods for adding, removing, and getting child objects.

## Structure

Components declare the interface for all composition objects

Composite objects define the behavior for components that have children and also store the child components

Leaf is the primitive object in the composition, and a leaf has no children

Note that the composite object has two responsibilities: functionality for building the collections/branches of objects, and performing an operation--this goes agains the single responsibility principle

Defining the child management in the composite increases type safety as attempts to add/remove from a leaf will fail at compile time for statically-type languages. This is a cost to transparency because in the initial pattern diagram all components can be treated uniformly.

A component is any object in a composite tree structure; components may be leaf nodes or other composites.

Example: Filesystem

- Component: FileSystemComponent (has show() method)
- Leaf: File (has show() method)
- Composite object: Directoy (has a component list, add(), remove(), and show() methods)

File and Directory both implement the FileSystemComponent interface

The file and directory objects are used to create a tree structure of files and containers.
# Java for OOAD

## History: Simpler and Safer

- James Gosling, one of Java's main designers at Sun, emphasized that Java was both simpler and safer than C++

- Simpler: Removed language features that added complexity or were easily misused: pointer and pointer arithmetic, notion of "friend" classes, ability to define new operators. No explicit memory management due to garbage collector.

- Safer: Interpreted (runs in a protected virtual machine), memory safe access and allocation, built-in bounds checking and no pointers made it more difficult for malicious code to be written to "hack" the language's runtime system.

- Java's goal was to "write once, run anywhere." Java code could run wherever a JVM existed, including for embedded devices.

## Support for Object Orientation

- Java has a clean object model while still providing access to primitive types (ints, floats, etc.)
- Single inheritance object-oriented model plus interfaces
- Extensive class library and industry standard tools

- Great language to clearly see OO in practice
    - Exceptions: multiple inheritance, newer extended interface capabilities

- Generally readable code, related to "egoless" programming

## Java is Interpreted (sort of)

Java source files (.java) are compiled into binary Java bytecode files (.class) which are read and interpreted by the Java Virtual Machine; the JVM may identify portions of the bytecode that can be translated straight into machine code and then executed directly by the host OS. JVMs regularly include just-in-time (JIT) compilation to speed up execution of more frequently used program elements.

## Performance

- In its early years, Java suffered from performance problems vs code in other languages that had been directly compiled for a particular OS/machine

- Now, extensive use of JIT compilation has largely eliminated these concerns

- Java provides excellent performance for many frameworks across many domains

- Provides native code interface (access to C libraries) to gain additional speed if needed

## Java Applets: Rise and Fall

Java applets were designed for web pages to run Java in a JVM in a browser and required a browser plugin to run; these over time proved to have security issues, so applets were deprecated and removed from Java 11.

## Fundamentals

At its simplest, a Java program is a collection of objects and a main program.

- In most Java applications, the main program creates an object or two and sends messages to those objects to get the system started. These objects then communicate with other objects to achieve the objectives of the program.

- Main itself is a relatively non-OO routine used to bootstrap objects. A good practice is to limit logic performed in main to instantiating and initializing the objects that will do the real application work.

Public class HelloWorld is contained in a file called HelloWorld.java. Generally, each Java file will have a single public class in it (you can have multiple classes, but only one can be public). Compiling this file produces a new file called HelloWorld.class. If Java's interpreter is passed the name HelloWorld, it will look for that name's associated class file, then looks for a static main method that takes an array of strings as a parameter; execution begins with the first line of the main routine.

main() is static because at the start of execution, no program-supplied objects have been created; there is no instance of HelloWorld to invoke methods on, so the interpreter reads in the class, locates the statically-available main() method, and invokes it.

## Packages

One Java mechanism for grouping classes is known as the package. Packages enable the creation of large-scale software systems written in Java.

- A class can declare itself to be part of a package with the package keyword followed by a dotted name. For example: package mypack.foo

- The previous statement declares that there is a top-level package called mypack that contains a subpackage called foo. The class that uses this statement is a member of package foo.
    - Top-level packages "java" and "javax" are reserved
    - Java has some conventions around package names

This also prevents name clashes: 
    - import foo.Employee
    - import bar.Employee

Classes in the same package can "see" each other with no need for import statements

Everything in the package java.lang is automatically imported into all Java programs

## Jar Files

A "file of files." If using external libraries, you will need to know how to bring .jar files into your IDE, where to place them, etc. and this differs from IDE to IDE

The jar command creates .jar files
    - jar cvf <file.jar> directory <-- creates a .jar file containing the contents of a directory
    - jar tvf <file.jar> <-- prints a table of contents for .jar file
    - The syntax is similar to the Linux "tar" command

The -classpath or -cp option is used by:
    - The javac compiler to allow files to access classes in a jar file during compilation
    - The Java JVM interpreter to locate classes in jar files that are needed during runtime

When used with the "java" command we must be sure to include all directories that we need, including the current directory, in order to ensure that the interpreter can find everything it needs to execute the given program.

## Java Directory Structures

Java source directories usually include subdirectories for .class files (bytecode) and .java files (source code)

IDEs usually automatically arrange file structures this way for sample and template code, such as src/ and out/

## Defining Java Classes

- All classes in Java extend from java.lang.Object, which defines a set of methods that can be invoked on any Java object

public class Employee {

}

is the same as:

public class Employee extends java.lang.Object {

}

## Single Class Inheritance

After java.lang.Object, classes can extend via single inheritance. All Java classes have one and only one parent.

- **extends** is the inheritance keyword

- **implements** is the interface reference keyword

- To allow a class to have more flexibility with respect to its type, Java provides the notion of adding interface references. Multiple interface names can appear after implements

- **instanceof** is an operator that returns a boolean; returns if an object is an instance of a specific class

## Classes and Interfaces

When a class implements an interface, the compiler requires that all methods defined in the interface appear in the class; if not, the class must be declared abstract and a subclass must implement the missing methods.

## Classes and Constructors

Constructors

- When a new instance of a class is created, its constructor is called to perform initialization 
- A constructor looks like a method that has the same name as the class but with no return type specified
- If you do not define a constructor, Java creates a default constructor with no arguments (this calls the default constructor of the superclass)
- The purpose of a constructor is to initialize an object
- Constructors can have arguments
    - If you want to use them, simply pass in the arguments when creating a new object
    - public PhDStudent (String name) {

    }
    is invoked with the call
    - PhDStudent bruce = new PhDStudent("Bruce");

If you don't call super() on the first line of the constructor, then Java inserts a call to the default constructor of the superclass.

Destructors

- Java is garbage collected, so no destructors; no guarantee when an object will be destroyed
- You can use a method, finalize, that is called when an object is destructed, but when this happens is not under program control
- There is a convention of creating a close method to indicate a class is closed and ready to be destructed. This is not necessary, as when you release the last reference to an object, the garbage collector may collect it.

## Accessibility

- Java supports several layers of accessibliity for data and methods in classes
- By default, the access is open within the package (package-private, i.e. public inside the package)
- Accessibility keywords include:
    - private (access only within the original class)
    - protected (access within original class and subclasses--the inheritance hierarchy of a class)
    - public (all access allowed)

## Java 8 Changes

- Default and static methods for interfaces
    - Using the **default** keyword in an interface method definition tells the implementing class it is not mandatory to provide an implementation. You can decide to override it or just use the default implementation.
    - Using the **static** keyword in an interface method allows an implementing class to call the method directly from the interface (without implementing it), and also allows the interface to use the static method in default method implementations

- **Lambda** expressions, which may change the way some interfaces are implemented
    - Lambda expressions are functional interfaces defined in-line
    - They can be passed as objects and can be created without belonging to a class

- The Diamond Problem: Because Java allows multiple implementations of interfaces in a class, it's possible to create a version of the diamond problem.

- Example: If two interfaces both provide default methods for a method called log, the implementing class would have to override log to avoid a compile time error due to the multiple implementations

## Anonymous Classes

Anonymous classes allow you to define a class at runtime to specify what happens when a particular event occurs

- Common when implementing something with a lot of instance variations, say elements of a graphical user interface
    - A button gets clicked and we need an instance of java.awt.event.ActionListener to handle the event
    - We could implement this handler in a separate file as a class that implements ActionListener that specifies what to do
    - We would then create an instance of that class and associate it with the button

    - The problem: what if you have 10 buttons that all require different implementations of ActionListener? You would have to create 10 different .java files to specify all the logic; not scalable

    - The solution: anonymous classes--create the ActionListener instances as needed

- Anonymous classes are defined "in-line" by using the new keyword; and because we are both defining a class and creating a new instance of it, we then provide a class or interface name with parentheses and an open bracket, followed by method definitions and a closing bracket

- The compiler will then define a new class, compile it to bytecode, and at runtime the interpreter will create an instance of this unnamed (anonymous) class

## Generics

Java provides a way to do "generic" data structures and components

- In procedural languages, we used to have to implement collections like this:
    - list of String, list of Integer, list of Employee; each list/data structure was written with a specific type of content in mind

This is not strictly necessary since the API and semantics of the data structure could be independent of its contents. Type placeholder inside of a definition.

Example: List of Strings

List<String> strings = new LinkedList<String>()

Passing "String" inside of the angle brackets tells the interpreter to create a version of List where E (the type) gets replaced by String

Java provides object wrapper classes like Integer (vs the primitive type int) to give you integer methods that you can use, but can automatically change between int and Integer as needed. This is called auto-boxing.

## Java GUI Tools

JavaFX is the recommended framework, including the design tool called Scene Builder
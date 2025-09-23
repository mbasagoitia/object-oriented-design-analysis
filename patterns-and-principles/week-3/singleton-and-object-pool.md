# Singleton

Used to ensure that only one instance of a particular class ever gets created and that there is just one (global) way to gain access to that instance.

Consider this method of creating only a single instance of a ball:

public class Ball {
    private static Ball ball;
    private String color;

    private Ball (String color) {
        this.color = color;
    }

    public void bounce() {
        System.out.println("boing");
    }

    public static synchronized Ball getInstance(String color) {
        if (ball == null) {
            ball = new Ball(color);
        }
        return ball;
    }
}

We have a private constructor and a static Ball reference that only gets instantiated if it doesn't already exist.

This is a typical singleton pattern:

- private constructor
- private static instance variable to store the single instance
- public static method to gain access to that instance
- this method creates the object if needed and returns it

## Variations and Issues

The above code ignores the fact that a parameter is being passed in; if a red ball is created, all subsequent requests for a green ball are ignored.

The solution to this problem might be to change the private static instance variable to a Map:

- private Map<String, Ball> toybox = new Hashmap();
- then check if the map contains an instance for a given value of the parameter
- this ensures that only one ball of a given color is ever created

### Thread Safety

This code is not thread-safe. It is possible for two threads to attempt to create the singleton for the first time simultaneously. If both threads check to see if the static variable is empty at the same time, they will both proceed to create an instance and you will end up with two instances.

In Java, the easiest fix is to add the **synchronized** keyword to the getInstance() method--this prevents other threads from entering once a thread acquires a lock; it can be applied to objects, methods, or part of methods.

An alternative is to just make the singleton! Create a static instance and the JVM will create the unique instance before any threading issues come up. This is called **eager instantiation**, as opposed to **lazy instantiation**, which is when we delay instantiation until needed for the first time.

public class Singleton {
    // private constructor
    private Singleton() {}
    // instance of Singleton in a static "eager" initializer
    private static Singleton myInstance = new Singleton();
    // we know we have an instance, just return it
    public static Singleton getInstance() {
        return myInstance;
    }
}

## Enum Singleton

The JVM guarantees enums are only instantiated once, so they are thread-safe. Using the enum guarantees a single eager instance.

public enum BallSingleton {
    INSTANCE;
    private String color;

    BallSingleton() {
        color = "mystery";
    }

    public void setColor(String color) {
        this.color = color;
    }

    public String getColor() {
        return color;
    }

    public void bounce() {
        System.out.println("The " + color + " ball goes Boing");
    }
}

class Main {
    public static void main(String[] args) {
        BallSingleton ball = BallSingleton.INSTANCE;
        ball.bounce();
        ball.setColor("blue");
        ball.bounce();
    }
}

Output:
The mystery ball goes Boing
The blue ball goes Boing

# Object Pool

The object pool is a variant of the singleton pattern.

It allows some instance (x) of an object to be created up to some maximum number (m), where 1 < x <= m

In this case, each instance provides a reusable service (typically tied to system resources such as network connections, printers, etc.) and clients don't care which instance they receive.

When a client completes use of an object, it is returned to the pool so others may use it.

The pool object is a singleton which provides acquire and release methods to get references to and to return reusable objects. The pool creates reusable objects (in a lazy or eager fashion) or it is otherwise provided with a collection of reusable objects.

May want to use in multi-threaded applications where each thread is a computation resource.
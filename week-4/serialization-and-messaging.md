# Serialization and Messaging

## Messaging and Serialization

**Messaging** is defined as a method for integration to reliably deliver data and/or commands from one element of a system to another

Since messaging often takes place using strings or streams of data in bytes, we also need a process to convert objects, data, and commands to a byte stream--this is known as **serialization.**
    - Conversion from a byte stream back to a known object format is known as **deserialization.**

### Messaging

- Communicating between devices or with other connections generally takes the form of messages, data, packets that require attention in some form

- Whether your system is a Java-based set of communicating objects or an embedded IoT system using cloud-based microservice APIs, system communications is usually based on some form of messaging

- There are alternatives to messaging
    - Shared memory areas
    - Data storage such as a relational database
    - File systems

In most cases, we design our systems to send messages between objects in some format

#### Messaging Address, Assembly, and Architecture

- Messages mau require some form of addressing or other control information to be embedded within the data, often in a message header, to allow systems to help route the messages to their correct destination

- In some cases, message may be large enough that they require assembly and disassembly at different points, or the messages may need to be queued for processing as they move from senders to recipients

- The architecture used for messaging is a key system design choice; alternative design patterns include:

- publish/subscribe
- request/response
- fan-out
- point-to-point
- databus
- survey messaging

There are some standardized patterns for messaging, as well as message queuing tools. Some of these include ZeroMQ, RabbitMQ, and AWS SQS

### Serialization and Deserialization

Serialization is the conversion of the state of an object into a byte stream, and deserialization does the opposite

In Java, serialization is built-in with the Serializable interface. This lets you give that class a special ID for serialization.

- A class can implement the Serializable interface, and all objects of that class could be serialized and written to a data output stream; likewise, data received from the stream could be converted back into Person objects.

- Static fields belong to a class (not an object) and are not serialized
- The transient keyword is used to ignore class fields during serialization
- The JVM associates a version (long) number with each serializable class
- As best practice, a serializable class should its serialVersionUID

Python has an analogous serialization scheme known as pickling/unpickling with the pickle module, achieved through pickle.dumps() and pickle.loads()

#### Other Serialization Formats

Most languages provide functions or libraries for dealing with conversions between formats--CSV, JSON, XML, YAML
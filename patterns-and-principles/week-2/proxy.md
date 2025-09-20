# Proxy

Provides a surrogate for another object to control access to that object.

Use the proxy pattern to create a representative object that controls access to another object which may be:

- remote (remote proxy)
- expensive to create (virtual proxy)
- in need of securing (protection proxy)

One common use is the remote proxy, which provides what looks like local access (to a client) to a remote object (provided by a server). There are several forms/variations of proxy.

The problem: normally, we can just connect to a local object and call its methods. However, if the object we want to talk to isn't in the local process or memory, how do we make a connection and make it look as much like we are talking to a local object as possible? We still want to structure the code as if we are talking to a local object.

To do this, we create a proxy object that the client talks to. The connection details across to the remote object are encapsulated.

## Java RMI (Remote Method Invocation)

RMI provides a client helper and a service helper object, connected via an IP socket connection to allow a client object to call methods on a remote service object in a remote memory space.

To do this, RMI provides a registry service on the server's host, which lets the server tell the registry where the remote object is if anyone looks to make a connection.

Steps to use an RMI remote proxy:

- Define a remote interface (called subject) for both the real object and proxy object implementations; this way all interactions are using a common interface
- Implement the remote real object (implements subject)
- Implement the local proxy for that remote real object (also implements subject)
- Implement the RMI server that provides the real object
- Implement the RMI client that uses the proxy
- Start the RMI registry
- Run the server and register the real object with the RMI registry
- Run the client
    - Using the URL for the server object
    - Look up the remote object by its name in the RMI registry
    - Invoke the remote method on the remote object via the local proxy object

Data passed over the remote connection will need to be primitives or Serializable objects

Remote methods will throw RemoteException if something goes wrong

Java RMI is just one of many ways to establish messaging for proxy type connectivity

## Virtual Proxy

Used where creating or invoking the real subject is expensive; if the proxy can handle the issue, it will

Can be used for caching; proxy checks to see if we have already loaded some information, and if not, may provide something temporarily while the real subject gets the "real" information

Proxy looks a little like Decorator; the difference is that decorator is extending the behavior of a class, while proxy is controlling access to the class. You can combine proxy with factory to make sure clients instantiate the proxy object instead of instantiating the real subject you're controlling access to.

Proxy also looks a bit like adapter, since it sits in front of another object, but proxy implements the exact same interface as real subject, whereas adapter changes the interface of objects it adapts.

## Protection Proxy

Proxy verifies whether the request for an operation to be performed is valid/authorized, such as checking for valid identifiers or for access level permissions by user type, etc.

## Other Proxy Variations

- Firewall proxy: controls access to a set of network resources, protecting subjects from bad clients
- Smart reference proxy: provides additional actions when a subject is referenced, such as maintaining a reference count
- Caching proxy: a version of virtual proxy to maintain temporary storage that can be referenced rather than asking the subject to do an expensive task
- Synchronization proxy: provide safe access to a subject from multiple threads
- Complexity hiding/facade proxy: unlike facade, this proxy provides both an alternative interface and access control
- Copy-on-Write proxy: controls copying an object by deferring copy until required by a client (another virtual proxy variant)
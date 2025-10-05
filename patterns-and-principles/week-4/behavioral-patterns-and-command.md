# Behavioral Patterms

Manage behavioral variation and control flow, interaction and communication, and assignment of responsibility. Often focused on increasing cohesion and limiting coupling for objects requesting actions and objects performing actions.

Some behavioral patters:

- Observer
- Strategy
- Command
- State
- Template

## Command Pattern

Uses request objects (commands) to encapsulate invocation, delivering all the information needed to ask another object (receiver) to do something.

An intermediate object, the invoker, can control how the command is sent to the receiver (for queuing or prioritizing, for instance).

Besides standardizing the request structure, commands help separate objects responsible for actions from objects requesting and invoking actions.

They are often used for undo/redo operations by looking at the prior executed command(s) to determine methods for the undo/redo of an operation.

### Example

Consider a diner

- Client: customer
- Command: order
- Invoker: waiter
- Receiver: cook

The customer creates one or more orders, the orders go to the waiter who will process them by selecting and delivering to a cook, and the cook receives the order and performs the operation requested.

Commands (requests) have a standard interface with one method: execute. These commands are instantiated by adding a reference to the receiver object, but that could be done elsewhere. If we implemented an undo/redo, the undo would also be in the command interface.

For example, all commands implement an Order interface that implement the execute command--OrderSteak takes in a cook argument and execute() calls cook.prepareSteak(). The waiter (invoker) has a reference to (is passed) order objects, and calls order.execute(), the standard interface, in a submitOrder method.

The invoker could make independent decisions about when to submit orders and what receivers they should go to, for instance.

Typical flow:

1. Start at client
2. Client object creates a command/request object, which needs to know the target receiver and receiver methods (which actions the receiver should execute)
3. Command object defines execute(), which invokes specific receiver methods
4. Client object calls invoker.setCommand(command), which tells the invoker "I have a command object for you"
5. Invoker calls command.execute()
6. Receiver executes the receiver methods in the command when the invoker calls them

- Command interface defines common command methods

May want to create a "no-operation" command so that the client doesn't have to handle null cases:

NoCommand implements Command {
    public void execute() { }
}

AKA "null object pattern"

The standard command object has both execute() and undo(). Undo is usually a reversal of the execute action in some way.

Could create a macro object that accepts an array of commands that can be executed all at once

Command can also be used to queue requests--invoker places commands into a queue, then pulls commands from the queue and assigns them to available threads.

May also be used for logging requests, also store and load methods to protect against system failure. Can look up and execute incomplete commands in the order they were received.
# State Pattern

A way to create systems that have a state transition structure.

## State Machines

State machines are everywhere, very common in software, especially embedded systems.

A state machine-based system makes decisions based on its current state and transition events, changing behavior based on context (such as the environment and internal state settings).

State machines are like flow charts, where the elements in the flow chart are the states and the transitions are the arrows between them.

The commands that cause state machine transitions are likely asynchronous--they can occur at any time, and every state must be able to handle all possible transitions, even if they occur improperly. Often, improper transitions are just ignored and you just stay in the state you're in, or you may raise an error.

## State Pattern

Provides a clean way for an object to vary its behavior based on its current state. That is, the object's public interface doesn't change, but each method's behavior may be different as the object's internal state changes.

Definition: The State pattern allows an object to alter its behavior when its internal state changes; the object will appear to change its class.

Same UML structure as Strategy, but different intent.

- Create a state interface that has one method per state transition
- Create one class per state in a state machine. Each such class implements the state interface and provides the correct behavior for each action in that state.

The state machine has the ability to set the state.

Each state transition is handled by the current state object--that handling may include setting a new current state object for future transitions.
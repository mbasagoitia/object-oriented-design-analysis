# Refactoring

A controlled technique for improving the design of an existing code base. In essence, it is applying a series of small behavior-preserving transformations, each of which is "too small to be worth doing." However, the cumulative effect of each of these transformations is quite significant. By doing them in small steps, you reduce the risk of introducing errors. You also avoid having the system broken while you are carrying out the restructuring, which allows you to gradually refactor a system over an extended period of time. It is easy to make mistakes during refactoring!

Key points from the introduction of Refactoring:

When you have to add a feature to a program but the code is not structured in a convenient way, first refactor the program to make it easy to add the feature, then add the feature.

Before you start refactoring, make sure you have a solid suite of tests; these tests musts be self-checking.

Refactoring changes the program in small steps, so if you make a mistake, it is easy to find where the bug is. 

When programming, follow the camping rule: always leave the code base healthier than when you found it.

A true test of good code is how easy it is to change it.

When to refactor?

- Rule of three: third time you do something similar, refactor
- If code is a mess but doesn't require modification, leave it
- If code needs to be rewritten, not refactored (judgement call)

## Problems with Refactoring

- Management perceptions
- Slowing down new features 
- Published interfaces (already in use by customers)
- Branches
- Testing
- Legacy code
- Databases and migration scripts
- Code ownership: before you refactor someone else's code, if you can, talk to them first 

## Potential Code Smells

- Mysterious name
- Duplicated code
- Long function
- Long parameter list
- Global data
- Mutable data
- Divergent change (one module changed in different ways for different reasons)
- Shotgun surgery (lots of edits to lots of classes for a single change)
- Feature envy (using someone else's methods a lot)
- Refused bequest (poor method inheritance)
- Comments (as deodorant)
- Data clumps
- Primitive obsession
- Repeated switches
- Loops
- Lazy elements (largely unused)
- Speculative generality (YAGNI)
- Temporary field
- Message chains
- Middle man
- Insider trading
- Large class
- Alternative class with different interfaces
- Data class

## Common Refactorings

- Extract function and inline function
- Extract variable and inline variable
- Change function declaration for clarity
- Encapsulate variable (visibility/access)
- Rename variable (meaningful names)
- Introduce parameter object
- Combine functions into class
- Combine functions into transform
- Split phase (parsing parameters before using them)

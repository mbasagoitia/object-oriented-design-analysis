# Testing and Test-Driven Development for OOAD

## Definitions

- Verification: esnuring oyur code meets engineering requirements
- Validation: ensuring your code meets application/user expectations
- Testing: running a program on selected inputs and checking the results
- Formal verification: constructing a proof that a program is correct
- Z motation: a formal specification for describing and modeling business requirements for a program with relational algebra--allows code to be "correct by construction"

## Software Quality Expectations

- Typical industry software: 1 - 10 defects/kloc <--- kloc = 1,000 lines of code
- High-quality validation: 0.1 - 1 defects/kloc
- The very best, safety-critical validation 0.01 - 0.1 defects/kloc

## Software Testing is Difficult

- Exhaustive testing is almost always infeasible
- Haphahazard testing, what a lot of us do, has us try typical operations to see what it does; doesn't find all bugs
- Random or statistical testing doesn't work well for software

## Software vs Physical Systems

- Software behavior is discontinuous; a system may seem to work fine in normal use and input data, and then fail unexpectedly for some specific combination of data

- Physical systems often provide early evidence that failures are occurring (cracks, discolorations, changes in behavior). Statistical testing may find failures before they occur.

## Different Testing Perspectives for Systems

- Each level of code has a different perspective on test and test approaches, from unit tests of individual modules, to sub-system tests, all the way through acceptance testing by users and stakeholders

## Software Development vs Software Testing

- Testing is often a difficult mental transition for a developer
    - As a developer, the goal is to make the program work
    - As a tester, you want to make it fail

Often, we develop in a "test-after" fashion. There are several issues with this! Testing cycle receives less focus than it should, and can throw off schedules and expectations. Highlights need for early planning and testing.

## Test-First Development

- Taking "test-with" further; there is a recognized best practice of "test-first" development, which is the basis of test-driven development (TDD)

Steps:

- Write a test case specification for the next functionality you want to add (based on system requirements)--parameters, constraints, return values
- Write the functional code until the test passes
- Refactor both old and new code to make it well-structured

- A side benefit of writing test cases is examining the software requirements and specifications for correctness and completeness--your test work might find specification defects

## OOAD and TDD

Generally, OOAD is a conceptual exercise that leads to detailed specification and implementation, whereas TDD is details-first development (tests before code)

### Suggested Approach

- Define the problem 
- Draw the problem
- Identify the problem's entities (the classes)
- Create the entity hierarchies (connections)
- Identify entity responsibilities  (communication/messaging)
- Write the tests for these entities 
- Check that they fail as expected
- Write your code
- Refactor/repeat/refine

- OOAD: conceptual foundation
- TDD: specification/implementation technique

## White Box vs. Black Box Testing

Black box testing: checks the accuracy of your system to its specifications; the internal implementation is not considered  
    - Typical to QA testing that does not have access to information about software internals
    - Reusable for future testing, as they are looking at general functionality

White box testing: analyzes a system by checking its internal coding; this helps find bugs from the design level to identify and eliminate them
    - Also known as clear or glass box testing due to internal visibility
    - Used in unit and integration tests, and often include use of test automation tools
    - May require revisiting or revision if internal structure changes

## Test Coverage

Coverage: how thoroughly does a test assess a program

Types:

- Statement coverage
    - Every statement run by a test case
    - 100% statement coverage is a common goal, but may be difficult for some hard to reach conditional code
- Branch coverage
    - Every conditional statement in the program, are the conditional branches followed by a test case
    - 100% branch coverage is also a good testing goal
- Path coverage
    - Every possible combination of branches (all paths through the program) driven by test cases
    - 100% path coverage is usually infeasible due to the many input combinations a system may see

One standard approach to testing is to add tests until reachable statement in the program is executed by at least one test case

Statement coverage is usually measured by test or code coverage tools, which counts the number of times each statement is run in a test environment
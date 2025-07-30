# Developing Software: Requirements

## Best Practices for Requirements

- Clarity, no ambiguity
- Be as brief as possible
- Doable or actionable
- Prioritized simply (high/medium/low)
- Requirements should be testable
- Consistent form and terminology
- Avoid using conjunctions like "and"
- Use precise words to convey specific things ("shall" = must do, "will" = a fact, "should" = a goal)
- Well-written requirements can be a single source of truth for the software team to reference

Common requirements gathering tools:

- Jira/Confluence
- DOORS
- Azure DevOps
- Trello
- ReqView

However, the problem of eliciting requirements is difficult.

- May be incomplete and do not tell the whole story
- Requirements are often wrong
- Requirements and users are misleading
- Users may be non-technical and may not understand the range of options that could solve their problem
- Requirements always change!
    - A user's needs or the product focus may change over time
    - As they learn more about a new problem domain, a developer's ability to generate better solutions to the original problem will increase
    - The system's environment changes
    - New hardware, new external pressure, new techniques

## Agile

- Many developers view changing requirements as a bad thing
- Luckily, this view has changed over time
    - Agile software methods tell developers to welcome change
    - Agile approaches recommend a set of techniques, technologies, and practices for developers to follow to remove the fear and burden of change
    - OO analysis, design, and programming techniques provide you with powerful tools to support change to software systems in a straightforward manner

## Supporting Requirement Changes in Code

However, this doesn't mean that we stop writing requirements

- The lesson is that we need to improve both the way we design our systems and design our code such to allow change to be managed and requirements to be met

- Our requirements may take different forms
    - Agile methods make use of "user stories"
    - Other lifecycle methods make use of requirements documents and/or use cases (scenarios that describe desired functional characteristics of the system)

- Requirements (in whatever form) provide understanding of the problem domain through analysis

- We can then design our system to address the requirements while allowing for inevitable changes

## "Good Code"

(One definition from MIT)

- Response to change (code design, test and regression support)
- Safe from bugs (verified and validated, able to confirm changes with tests)
- Easy to understand (clarity of design and responsibilities, adequate documentation)
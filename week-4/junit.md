# JUnit for OOAD

## Testing Trends and Unit Testing

There is significant variation in test approaches between organizations

Testing tools like Jira, Selenium, Postman, and JUnit continue to be used in software testing

Automated test APIs, user interfaces, and other test operations continue to increase with stronger AI tools

The most common testing in software projects is **unit testing**, followed by functional and integration tests

## Unit Testing Best Practices

**Arrange, Act, Assert**

- Arrange: get things ready to test; instantiate an object or generate data
- Act: decide what one action you'll perform to check
- Assert: use an appropriate check (like AssertEqual) to see if your code did what you expected

One assert vs multiple assert per test method
    - Debatable--one assert is usually preferred for failure visibility

Avoid test interdependence
    - Tests sould be self-contained and not dependent on each other
    - Ideally, each test should handle any setup or tear down needed

Short and visible tests
    - Make it easy to see what went wrong
    - Write the test to know exactly what failed if test doesn't pass

If the arrange step is hard, that may be a code smell
    - May point to a non-modular design

Focus on boundary, empty, or error cases and combined behavior

Run tests with every build
    - Part of a standard DevOps/build process that includes any tests added

## Automated and Regression Tests

If you're using a test process that results in unit tests, you could run those at every build in your DevOps cycles; this is automated testing; this is opposed to automatic test generation, which is a continuing target for active computer science research

Regression testing refers to test cases to verify a modification or bug fix was successful  (to keep your code from regressing or getting worse)

Suites of unit and regression tests grow as code matures

The greatest value of these tests is when the tests are run often and automatically for builds, as in a DevOps flow

## Test Frameworks for Unit Testing

A unit test harness is a software package to help assess code correctness

Such packages can provide:

- A common language to express test cases
- A common language to express expected results
- Access to the features of the production code programming language
- A place to collect the unit test cases for the project, system, or subsystem
- A mechanism to run the test cases, either in full or in partial batches
- A concise report of the test suite success or failure
- A detailed report of any test failures

## Mocks and Test Doubles

Test frameworks and other tools often support the development of a mock or test double object

A mock allows a test case to describe the calls expected from one module to another

During test execution, the mock checks that all calls happen with the right parameters and in the right order

The mock can also be instructed to return specific values in proper sequence to the code under test

A mock is not a simulator, but it allows a test case to simulate a specific scenario or sequence of events

There are many Java test frameworks available, including JUnit, Selenium, TestNG, Cucumber, Serenity, Mockito, Spock, and JBehave

## Common JUnit 5 Assertions

- assertArrayEquals
- assertEquals and assertNotEquals
- assertTrue, assertFalse
- assertNull, assertNotNull
- assertSame, assertNotSame (same object or not)
- fail
- assertAll

## Common JUnit 5 Annotations

- @Test: marks a test method in a class; the method will be treated like a test, get executed by the test engine, get a row in the reporting, etc.
- @TestFactory: a method marked with this annotation will be used to create test cases at runtime
- @DisplayName: makes reports readable with supplied test names
- @BeforeAll/@BeforeEach: lifecycle methods executed prior to running tests
- @AfterAll/@AfterEach: lifecycle methods for cleanup, executed after the tests
- @Tag: tags a method to separate tests into suites
- @Disabled: makes JUnit skip this test
- @Nested: use with an inner class to control the order of tests
- @ExtendWith: use to enhance the execution--provide mock parameter resolvers or specify conditional execution
# Task 1

Task: You are tasked with designing a maintainable test suite for a new iOS app
project. The app is expected to have a large user base and complex
functionality, including networking, data storage, and user interactions. Your
test suite should cover all critical functionality and ensure high test
coverage. Design a test pyramid with non-overlapping coverage areas, and explain
your rationale for each level.

Solution: At the base of our test pyramid, we will have a large number of unit
tests that cover our code's functionality at the method and class levels. These
unit tests will be designed to catch bugs as soon as possible and help us
isolate and fix them quickly. We will aim to achieve close to 100% test coverage
at this level.

In the middle layer of our pyramid, we will have a moderate number of
integration tests that cover our app's key features and interactions. These
tests will ensure that our app's core functionality is working as expected and
that key user flows are not broken. These tests will be non-overlapping with our
unit tests, and we will aim to achieve at least 90% test coverage at this level.

At the top of our pyramid, we will have a small number of end-to-end tests that
cover the most critical user journeys of our app. These tests will verify that
our app's functionality is correctly integrated and working together as a whole.
We will aim to achieve at least 80% test coverage at this level.

Rationale: Our test pyramid design ensures high test coverage with
non-overlapping coverage areas. At the unit test level, we cover code
functionality at the method and class level, which is critical to catch bugs
early and isolate and fix them quickly. At the integration test level, we cover
our app's key features and interactions, ensuring that our app's core
functionality is working as expected and that key user flows are not broken.
Finally, at the end-to-end test level, we cover the most critical user journeys
of our app, verifying that our app's functionality is correctly integrated and
working together as a whole.

Differences that indicate development to Senior 1 from Middle 3:

-   The Senior 1 developer understands the importance of designing a
    maintainable test suite for a large, complex app, whereas the Middle 3
    developer may have focused more on individual testing tasks.
-   The Senior 1 developer has a deep understanding of the different levels of
    testing and the rationale for each level, whereas the Middle 3 developer may
    have focused more on writing and running tests without much consideration
    for their purpose.
-   The Senior 1 developer has a more comprehensive understanding of test
    coverage and how to achieve it, whereas the Middle 3 developer may have
    focused more on achieving high coverage without considering the different
    levels of testing needed to achieve it.

# Task 3

## **Task**

You're working on a new project and you're responsible for defining the test
strategy. Define a maintainable test pyramid with non-overlapping coverage areas
for this project. Assume the project is an iOS app that allows users to browse
and purchase items from an online store.

## **Solution**

As a senior iOS developer, you should have a good understanding of the test
pyramid and how to apply it to different types of applications. Here's an
example of a maintainable test pyramid with non-overlapping coverage areas for
the given project:

1. **Unit tests (Foundation):** These tests should cover the business logic of
   the application. For example, testing the calculations for discounts or taxes
   when adding items to the cart. These tests should be fast and isolated from
   external dependencies.
2. **Integration tests (Foundation & UIKit):** These tests should cover the
   interaction between different components of the application. For example,
   testing the communication between the networking layer and the data
   persistence layer. These tests should be slower than unit tests and can
   include some external dependencies.
3. **UI tests (XCUITest):** These tests should cover the user interface of the
   application. For example, testing the layout of the product detail page or
   the behavior of the checkout flow. These tests should be the slowest and can
   include external dependencies such as the network or backend.

By using a test pyramid, we can ensure that our test suite is maintainable and
provides fast feedback for developers. Additionally, by having non-overlapping
coverage areas, we can ensure that each layer of the pyramid tests different
aspects of the application, reducing the chance of missing critical bugs.

As a senior iOS developer, you should be able to justify your choices and
explain why you chose a particular approach over others. You should also be able
to discuss trade-offs and the impact of your choices on the project as a whole.

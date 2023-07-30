# Task 3

Task: Write a unit test for a function that calculates the factorial of a given
number.

Function signature:

```swift
func factorial(_ n: Int) -> Int {
    // implementation
}
```

Solution:

```swift
func testFactorial() {
    XCTAssertEqual(factorial(0), 1)
    XCTAssertEqual(factorial(1), 1)
    XCTAssertEqual(factorial(5), 120)
    XCTAssertEqual(factorial(10), 3628800)
}
```

In this task, the developer is expected to write a unit test that checks if the
**`factorial`** function works as expected for different inputs. This task
requires the developer to have an understanding of how to write unit tests and
how to use XCTest framework, as well as basic programming knowledge such as
loops and conditionals. To solve this task, the developer needs to create a test
function and call the **`XCTAssertEqual`** function with expected and actual
values.

The main difference between this task and the previous one is that this task
requires the developer to write a more complex test that involves creating a
function and checking its output. This task also requires the developer to have
a better understanding of the XCTest framework and how to write effective unit
tests.

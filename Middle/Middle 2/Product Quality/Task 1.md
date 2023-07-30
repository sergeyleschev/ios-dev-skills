# Task 1

Task: Given a function that returns the factorial of a given number, write a
unit test for it using XCTest framework.

Function signature:

```swift
func factorial(_ n: Int) -> Int {
    if n == 0 {
        return 1
    }
    return n * factorial(n-1)
}
```

Solution:

```swift
import XCTest

class FactorialTests: XCTestCase {

    func testFactorial() {
        XCTAssertEqual(factorial(0), 1)
        XCTAssertEqual(factorial(1), 1)
        XCTAssertEqual(factorial(5), 120)
        XCTAssertEqual(factorial(10), 3628800)
    }
}
```

Differences between Middle 1 and Middle 2 level:

At the Middle 2 level, developers are expected to have a deeper understanding of
unit testing and TDD, and be able to write more complex and thorough unit tests.
They should also be able to use test-driven development to guide their code
implementation, and have experience with testing frameworks beyond XCTest.
Additionally, they should have experience writing and executing UI tests to
ensure the quality of their app's user interface.

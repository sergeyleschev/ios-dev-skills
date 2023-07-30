# Task 3

Test Task: You are tasked with writing a unit test for a function that
calculates the sum of two integers. The function takes two integer parameters
and returns the sum of them. Write a test case for this function using XCTest
framework.

Solution:

```swift
// Function to test
func sum(_ a: Int, _ b: Int) -> Int {
    return a + b
}

// Test Case
import XCTest

class SumTests: XCTestCase {
    func testSum() {
        XCTAssertEqual(sum(5, 3), 8, "Sum of 5 and 3 should be 8")
        XCTAssertEqual(sum(-5, 3), -2, "Sum of -5 and 3 should be -2")
        XCTAssertEqual(sum(0, 0), 0, "Sum of 0 and 0 should be 0")
    }
}

// Output:
// All tests pass
```

Differences from Junior 3 to Middle 1 level:

-   Ability to write effective and comprehensive unit tests using XCTest
    framework.
-   Understanding of Test Driven Development (TDD) principles.
-   Knowledge of UI testing and ability to write UI tests.
-   Familiarity with code coverage tools and ability to use them to ensure
    maximum code coverage.

# Task 2

Task: Write unit tests for a function that takes in two integers and returns
their sum. The function should handle both positive and negative numbers.

Solution:

```swift
func testSumFunction() {
    // Test with positive numbers
    XCTAssertEqual(sum(2, 3), 5)

    // Test with negative numbers
    XCTAssertEqual(sum(-2, -3), -5)

    // Test with a positive and a negative number
    XCTAssertEqual(sum(2, -3), -1)

    // Test with zero
    XCTAssertEqual(sum(0, 0), 0)
}

func sum(_ a: Int, _ b: Int) -> Int {
    return a + b
}
```

To indicate the development of a junior 2 to a junior 3 level, the interviewer
should look for the following differences:

1. Ability to write more complex functions and algorithms.
2. Familiarity with more advanced concepts, such as closures and protocols.
3. Improved understanding of the app architecture and ability to refactor code
   for better performance and maintainability.
4. Understanding of debugging tools and techniques, such as breakpoints and
   console logs, and the ability to use them to find and fix issues.

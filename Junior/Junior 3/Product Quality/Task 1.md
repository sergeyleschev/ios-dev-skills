# Task 1

Task: Write a unit test to verify that a function that calculates the average of
an array of integers returns the correct result for various input arrays.

Solution:

```swift
func testAverageCalculator() {
  let array1 = [1, 2, 3, 4, 5]
  let array2 = [10, 20, 30, 40, 50]
  let array3 = [0, 0, 0, 0, 0]

  XCTAssertEqual(average(of: array1), 3.0)
  XCTAssertEqual(average(of: array2), 30.0)
  XCTAssertEqual(average(of: array3), 0.0)
}

func average(of numbers: [Int]) -> Double {
  guard !numbers.isEmpty else { return 0 }

  let sum = numbers.reduce(0, +)
  return Double(sum) / Double(numbers.count)
}
```

In this task, the developer is expected to write a unit test for a function that
calculates the average of an array of integers. This task requires the developer
to have an understanding of unit testing, and how to write test cases using
XCTest. Additionally, the developer should have knowledge of arrays and loops,
as well as the ability to write simple functions.

At the Junior 3 level, the interviewer should look for the following skills:

1. The ability to write concise and well-structured code.
2. Strong understanding of testing concepts and ability to write comprehensive
   test cases.
3. Proficiency in basic algorithms and data structures.
4. Familiarity with debugging tools and techniques.
5. Good understanding of Swift language features and syntax.

In comparison to Junior 2, the Junior 3 developer should be able to write more
complex functions and algorithms, and have a better understanding of the Swift
language. They should also be able to write more advanced test cases that cover
edge cases and unexpected input.

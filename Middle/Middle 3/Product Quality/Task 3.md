# Task 3

Task: Write unit tests for a function that sorts an array of integers in
ascending order. The function should return a new array with the sorted
integers.

Solution:

```swift
func testSortArray() {
    let unsortedArray = [3, 2, 1, 5, 4]
    let sortedArray = sortArray(unsortedArray)
    XCTAssertEqual(sortedArray, [1, 2, 3, 4, 5], "Array not sorted correctly")
}

func sortArray(_ array: [Int]) -> [Int] {
    return array.sorted()
}
```

Differences that indicate the development of the developer to the level of
Middle 3 from the level of Middle 2 might include:

-   Writing more complex unit tests that test multiple functions or scenarios
-   Using test-driven development to write new code and test cases
    simultaneously
-   Implementing more advanced testing frameworks or methodologies, such as
    property-based testing or mutation testing
-   Ensuring code coverage targets are met and improving code coverage overall
-   Incorporating testing into a continuous integration/continuous delivery
    (CI/CD) pipeline for more comprehensive testing and faster feedback.

# Task 2

Task: Write a unit test for a function that takes in an array of integers and
returns the sum of all even numbers in the array.

Solution:

```swift
func testSumEvenNumbers() {
    let arr = [1, 2, 3, 4, 5, 6]
    XCTAssertEqual(sumEvenNumbers(arr), 12)
}

func sumEvenNumbers(_ arr: [Int]) -> Int {
    var sum = 0
    for num in arr {
        if num % 2 == 0 {
            sum += num
        }
    }
    return sum
}
```

In this task, we are testing a function that takes in an array of integers and
returns the sum of all even numbers in the array. We are writing a unit test to
verify that the function works correctly for a given input array. The test
function creates an input array and calls the **`sumEvenNumbers`** function to
get the sum of all even numbers in the array. It then uses the
**`XCTAssertEqual`** function to verify that the returned value is equal to the
expected sum of even numbers.

To solve this task, the developer needs to understand the concept of unit
testing and how to write unit tests in Swift. They also need to be able to write
a function that takes in an array of integers and returns the sum of all even
numbers in the array. Additionally, the developer should understand how to use
Swift's built-in assertion functions, such as **`XCTAssertEqual`**, to verify
that the function works as expected.

The difference between a Middle 2 and Middle 1 developer in this context could
be the level of complexity in the functions being tested. A Middle 2 developer
would be expected to be able to write unit tests for more complex functions,
such as those with multiple input parameters or functions that call other
functions. They would also be expected to have a better understanding of the
principles of Test Driven Development (TDD) and how to use it effectively to
write unit tests.

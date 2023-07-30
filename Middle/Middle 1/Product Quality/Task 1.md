# Task 1

Task: Write a unit test for a function that takes in an array of integers and
returns the sum of all the even numbers in the array.

Solution:

```swift
func testSumEvenNumbers() {
    let numbers = [1, 2, 3, 4, 5, 6]
    let expectedSum = 12
    let sum = sumEvenNumbers(numbers)
    XCTAssertEqual(sum, expectedSum, "Sum of even numbers is incorrect")
}

func sumEvenNumbers(_ numbers: [Int]) -> Int {
    var sum = 0
    for number in numbers {
        if number % 2 == 0 {
            sum += number
        }
    }
    return sum
}
```

In this task, the developer is expected to write a unit test for a function and
also implement the function. The function is simple and requires basic knowledge
of loops and conditionals. The developer is also expected to know how to use
XCTest framework to write unit tests.

The main difference between this task and the previous Junior level tasks is
that the developer is expected to have knowledge of writing unit tests and have
some experience with Test Driven Development (TDD). Additionally, the developer
is expected to have a deeper understanding of the XCTest framework and how to
write effective tests.

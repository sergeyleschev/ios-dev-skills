# Task 1

Task: Create a function that takes an array of integers as input and returns the
sum of all the even numbers in the array.

Solution:

```swift
func sumOfEvenNumbers(in array: [Int]) -> Int {
    var sum = 0
    for number in array {
        if number % 2 == 0 {
            sum += number
        }
    }
    return sum
}
```

Differences that indicate the development of the developer to the level of
Junior 2:

-   The developer is able to write functions that take parameters and return
    values.
-   The developer is comfortable using control flow statements such as **`if`**
    statements and **`for`** loops.
-   The developer is familiar with basic arithmetic operations such as **`%`**
    (modulo) to check for even numbers.
-   The developer is able to work with arrays and access elements using a
    **`for`** loop.

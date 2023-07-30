# Task 3

## **Task:**

Given an array of integers, write a function that returns the sum of all the odd
numbers in the array.

## **Requirements:**

-   The function should take an array of integers as input and return an integer
    representing the sum of all the odd numbers in the array.
-   If the input array is empty, the function should return 0.

## **Solution:**

```swift
func sumOfOddNumbers(in numbers: [Int]) -> Int {
    var sum = 0
    for number in numbers {
        if number % 2 != 0 {
            sum += number
        }
    }
    return sum
}
```

Differences from the Junior 1 level:

-   The solution uses a loop to iterate through each number in the array.
-   It checks whether each number is odd by using the modulus operator (**`%`**)
    to check whether the number is divisible by 2 with a remainder of 1.
-   If the number is odd, it is added to a running total of the sum of all odd
    numbers.
-   If the input array is empty, the function returns 0 to handle this edge
    case.

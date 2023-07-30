# Task 3

Task: Write a function in Swift that takes an array of integers and returns the
average of all the even numbers in the array. However, the function should use a
functional programming approach and not use any loops.

Solution:

```swift
func averageOfEvenNumbers(_ numbers: [Int]) -> Double {
    let evenNumbers = numbers.filter { $0 % 2 == 0 }
    let evenSum = evenNumbers.reduce(0, +)
    return Double(evenSum) / Double(evenNumbers.count)
}
```

Explanation: The function uses the **`filter`** method to create a new array
containing only the even numbers. It then uses the **`reduce`** method to sum up
all the even numbers in the array. Finally, it divides the sum by the count of
even numbers to get the average. This approach is functional because it uses
higher-order functions like **`filter`** and **`reduce`** instead of a
traditional loop.

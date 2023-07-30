# Task 1

Task: Write a function that takes in an array of integers and returns a
dictionary where the keys are the unique integers in the array and the values
are the count of each integer in the array.

Solution:

```swift
func countIntegers(in array: [Int]) -> [Int: Int] {
    var counts: [Int: Int] = [:]

    for element in array {
        counts[element, default: 0] += 1
    }

    return counts
}
```

Differences between Middle 2 and Middle 3:

-   Middle 3 developers should be able to handle more complex logic and
    algorithms involving dictionaries and sets.
-   They should have a better understanding of optimization and performance, and
    be able to optimize code for larger datasets.
-   They should also be familiar with more advanced concepts like closures,
    functional programming, and generics, and be able to apply them to solve
    problems more effectively.

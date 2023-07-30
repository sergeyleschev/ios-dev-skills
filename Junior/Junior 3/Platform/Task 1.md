# Task 1

Task: Given an array of integers, write a function that returns the two indices
that sum up to a given target. If no such pair exists, return nil.

Example:

```swift
let numbers = [2, 4, 6, 8]
let target = 10
let result = findIndices(numbers: numbers, target: target)
print(result) // (1, 3)
```

Solution:

```swift
func findIndices(numbers: [Int], target: Int) -> (Int, Int)? {
    var dict = [Int: Int]()
    for (i, num) in numbers.enumerated() {
        let complement = target - num
        if let index = dict[complement] {
            return (index, i)
        }
        dict[num] = i
    }
    return nil
}
```

Differences indicating development to Junior 3 level:

-   The task requires a deeper understanding of arrays, dictionaries, and sets
    and their usage in solving problems.
-   The solution involves more complex logic than the previous tasks, such as
    using a dictionary to store complements of numbers and their indices, which
    is a more advanced technique.
-   The time complexity of the solution is O(n), which is more efficient than
    some of the previous tasks.
-   The solution handles edge cases such as no pair of numbers summing up to the
    target value.

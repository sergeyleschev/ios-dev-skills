# Task 6

Task: Write a function that takes an array of integers and returns the count of
unique numbers in the array. The function should use a Set to keep track of
unique numbers.

Solution:

```swift
func countUniqueNumbers(in array: [Int]) -> Int {
    var set = Set<Int>()
    for number in array {
        set.insert(number)
    }
    return set.count
}
```

Difference from Middle level 1: In this task, the developer is expected to
understand the concept of Sets and how they can be used to efficiently keep
track of unique values. Additionally, the developer is expected to be able to
use Sets and the **`count`** method to solve the problem, demonstrating a deeper
understanding of collections and protocols like **`Hashable`**.

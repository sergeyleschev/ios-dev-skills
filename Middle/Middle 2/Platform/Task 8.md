# Task 8

Task: Given an array of integers, write a function to remove all duplicates and
return a new array with unique elements sorted in descending order.

Example: Input: [3, 4, 1, 6, 4, 1] Output: [6, 4, 3, 1]

Solution:

```swift
func removeDuplicatesAndSortDescending(_ array: [Int]) -> [Int] {
    var uniqueElements = Set<Int>()
    for element in array {
        uniqueElements.insert(element)
    }
    return Array(uniqueElements).sorted(by: >)
}

let array = [3, 4, 1, 6, 4, 1]
let uniqueElements = removeDuplicatesAndSortDescending(array)
print(uniqueElements) // [6, 4, 3, 1]
```

Difference from previous level: In this task, the developer needs to use a set
to remove duplicates, which requires understanding of value types and how they
can be compared for equality using the **`Equatable`** protocol. Additionally,
the developer needs to sort the array in descending order, which requires a good
understanding of arrays and sorting algorithms.

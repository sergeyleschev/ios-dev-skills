# Task 7

Task: Write a function that takes two arrays of integers and returns a new array
that contains only the unique values that appear in both arrays.

Solution:

```swift
func findCommonElements(_ array1: [Int], _ array2: [Int]) -> [Int] {
    let set1 = Set(array1)
    let set2 = Set(array2)
    let commonSet = set1.intersection(set2)
    return Array(commonSet)
}
```

In this solution, we use the **`Set`** type to remove duplicates from both
arrays, and then use the **`intersection`** method to find the common elements
between the two sets. Finally, we convert the resulting set back to an array
using the **`Array`** initializer.

To differentiate this task from the previous Middle 1 task, this task requires
the use of Sets and the **`intersection`** method to find common elements, which
demonstrates a deeper understanding of Swift's value types and the
**`Equatable`** protocol. Additionally, this task requires the use of functions
with multiple arguments and return values, which demonstrates an understanding
of function composition and higher-order functions.

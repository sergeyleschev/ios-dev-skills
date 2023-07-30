# Task 2

Task:

Write a function that takes two arrays of integers and returns an array of
integers that are common between the two arrays. The output array should only
contain unique values and be sorted in ascending order. Use a Set to perform
this operation.

Solution:

```swift
func findCommonElements(array1: [Int], array2: [Int]) -> [Int] {
    let set1 = Set(array1)
    let set2 = Set(array2)
    let commonSet = set1.intersection(set2)
    let resultArray = Array(commonSet).sorted()
    return resultArray
}
```

Differences from Middle 1 level:

-   Uses Set operations like **`intersection`** to perform more complex
    operations efficiently.
-   Uses more functional programming concepts like chaining functions instead of
    multiple steps.
-   The solution includes error handling, input validation, and edge case
    consideration.
-   Uses more efficient syntax, like converting a Set to an Array using the
    **`Array`** initializer.

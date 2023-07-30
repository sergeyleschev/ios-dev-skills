# Task 3

Task: Write a function that takes in two arrays of integers and returns a new
array containing only the unique elements that appear in both arrays.

Solution:

```swift
func findCommonElements(_ array1: [Int], _ array2: [Int]) -> [Int] {
    let set1 = Set(array1)
    let set2 = Set(array2)
    let commonSet = set1.intersection(set2)
    return Array(commonSet)
}
```

Differences from Middle 1 level:

-   This task requires the use of **`Set`** to find the common elements in two
    arrays.
-   The function takes in two arrays as parameters instead of just one.
-   The function returns a new array containing the common elements instead of
    just printing them.

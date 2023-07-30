# Task 3

Task: Given two arrays of integers, create a function that returns an array
containing the elements that appear in both arrays, without duplicates.

Example: Input: [1, 2, 3, 3, 4], [2, 3, 3, 5] Output: [2, 3]

Solution:

```swift
func findCommonElements(_ array1: [Int], _ array2: [Int]) -> [Int] {
    let set1 = Set(array1)
    let set2 = Set(array2)
    let commonElements = set1.intersection(set2)
    return Array(commonElements)
}
```

Differences that indicate development to the Middle 1 level:

-   The solution uses Swift sets to remove duplicates from the input arrays and
    find the common elements instead of using loops and if statements to
    manually compare the arrays.
-   The solution uses Swift's **`intersection`** method to find the common
    elements between the two sets instead of manually iterating over the sets
    and comparing their elements.
-   The solution uses the **`Array`** type constructor to convert the resulting
    set back into an array instead of manually iterating over the set and
    appending its elements to a new array.

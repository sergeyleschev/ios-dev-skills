# Task 5

Task: Given an array of integers, write a function to find the second smallest
element in the array.

Solution:

```swift
func findSecondSmallestElement(in array: [Int]) -> Int? {
    guard array.count > 1 else {
        return nil // there is no second smallest element in an array with less than 2 elements
    }

    var smallest = Int.max
    var secondSmallest = Int.max

    for element in array {
        if element < smallest {
            secondSmallest = smallest
            smallest = element
        } else if element < secondSmallest && element != smallest {
            secondSmallest = element
        }
    }

    return secondSmallest
}
```

Differences from Junior 1 to Junior 2:

-   Use of guard statements to handle edge cases and reduce nesting
-   Use of a for-in loop instead of a while loop for iterating over an array
-   Use of optional return type to handle the case where there is no second
    smallest element in the array

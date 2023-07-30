# Task 5

Task: Write a function that takes in two arrays of integers and returns a new
array that contains the unique elements of both arrays, in ascending order.

Solution:

```swift
func uniqueElementsArray(array1: [Int], array2: [Int]) -> [Int] {
    var set = Set<Int>()

    for element in array1 {
        set.insert(element)
    }

    for element in array2 {
        set.insert(element)
    }

    return Array(set).sorted()
}

//Example usage
let array1 = [3, 2, 1, 4, 5]
let array2 = [7, 6, 5, 4, 3]

let uniqueElements = uniqueElementsArray(array1: array1, array2: array2)

print(uniqueElements) //prints [1, 2, 3, 4, 5, 6, 7]
```

Differences from Junior 2 level:

-   This task requires the use of both arrays and sets, indicating a higher
    level of understanding of data structures.
-   The function returns a new array containing the unique elements of both
    arrays, indicating a higher level of logic and problem-solving ability.

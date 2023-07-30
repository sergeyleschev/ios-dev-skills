# Task 4

Task: Given an array of integers, write a function to return the index of the
first non-repeating element. If all elements are repeated, return -1.

Solution:

```swift
func firstNonRepeatingIndex(_ array: [Int]) -> Int {
    var dict: [Int: Int] = [:]

    for i in 0..<array.count {
        let num = array[i]
        dict[num, default: 0] += 1
    }

    for i in 0..<array.count {
        let num = array[i]
        if dict[num] == 1 {
            return i
        }
    }

    return -1
}

// Example usage
let array = [1, 2, 3, 2, 1, 4, 4, 5, 6, 6, 5]
let index = firstNonRepeatingIndex(array)
print(index) // Output: 2
```

In this task, the developer is expected to use basic knowledge of arrays and
dictionaries to solve the problem efficiently. The use of a dictionary to count
the occurrence of each element and the iteration through the array to find the
first non-repeating element are key skills that differentiate a Junior 3
developer from a Junior 2 developer. Additionally, the use of control flow
statements like **`if`** and **`for`** loops is also expected at this level.

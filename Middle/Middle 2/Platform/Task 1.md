# Task 1

Task: Write a function that takes in an array of integers and returns a
dictionary with the count of each integer in the array. If an integer appears
more than once in the array, its count should reflect the total number of times
it appears.

Solution:

```swift
func countIntegers(in array: [Int]) -> [Int: Int] {
    var dict: [Int: Int] = [:]
    for num in array {
        dict[num, default: 0] += 1
    }
    return dict
}
```

Differences from Middle 1 level:

-   The task is more complex and requires the developer to create a function
    that takes in a parameter and returns a value based on that parameter.
-   The solution uses the **`default`** parameter of a dictionary to handle the
    case where the key does not yet exist in the dictionary. This demonstrates a
    more advanced understanding of dictionaries and their behavior.
-   The solution uses a **`for`** loop to iterate through the input array,
    rather than relying on higher-order functions like **`map`** or
    **`filter`**. This demonstrates an understanding of different ways to
    iterate through arrays and perform operations on their elements.
-   The function name is more descriptive and follows Swift naming conventions.
    This demonstrates an understanding of the importance of clear and consistent
    naming conventions in code.

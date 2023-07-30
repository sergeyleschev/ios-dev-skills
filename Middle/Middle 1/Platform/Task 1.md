# Task 1

Task: Given an array of strings, create a function that returns a dictionary
where the keys are the strings in the array and the values are the number of
times each string appears in the array.

Example: Input: ["apple", "banana", "apple", "cherry", "banana", "apple"]
Output: ["apple": 3, "banana": 2, "cherry": 1]

Solution:

```swift
func countStringsInArray(_ array: [String]) -> [String: Int] {
    var dict = [String: Int]()
    for str in array {
        dict[str, default: 0] += 1
    }
    return dict
}
```

Differences that indicate development to the Middle 1 level:

-   The solution uses the **`default`** parameter of the dictionary subscript to
    avoid using optional unwrapping when accessing dictionary values.
-   The solution uses a **`for-in`** loop to iterate over the elements of the
    array instead of using a **`while`** loop with an index variable.
-   The solution uses a Swift dictionary instead of an NSArray or NSDictionary.

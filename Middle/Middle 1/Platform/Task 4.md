# Task 4

Task: Given an array of strings, create a function that returns a dictionary
where the keys are the strings in the array and the values are the lengths of
the strings.

Example: Input: ["apple", "banana", "cherry"] Output: ["apple": 5, "banana": 6,
"cherry": 6]

Solution:

```swift
func mapStringToLength(_ strings: [String]) -> [String: Int] {
    var dict = [String: Int]()
    for string in strings {
        dict[string] = string.count
    }
    return dict
}
```

Differences that indicate development to the Middle 1 level:

-   The solution uses a **`for-in`** loop to iterate over the strings in the
    array instead of using a C-style **`for`** loop or a **`while`** loop with
    an index variable.
-   The solution uses a Swift dictionary instead of an NSDictionary.
-   The solution uses the **`count`** property of the string to get its length
    instead of using a separate variable or method call to calculate the length.
-   The solution assigns the value directly to the dictionary instead of using
    the **`updateValue(_:forKey:)`** method.

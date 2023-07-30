# Task 2

Task: Given a string, create a function that returns a dictionary where the keys
are the characters in the string and the values are the number of times each
character appears in the string.

Example: Input: "hello" Output: ["h": 1, "e": 1, "l": 2, "o": 1]

Solution:

```swift
func countCharactersInString(_ str: String) -> [Character: Int] {
    var dict = [Character: Int]()
    for char in str {
        dict[char, default: 0] += 1
    }
    return dict
}
```

Differences that indicate development to the Middle 1 level:

-   The solution uses a **`for-in`** loop to iterate over the characters in the
    string instead of using a C-style **`for`** loop or a **`while`** loop with
    an index variable.
-   The solution uses a Swift dictionary instead of an NSDictionary.
-   The solution uses the **`default`** parameter of the dictionary subscript to
    avoid using optional unwrapping when accessing dictionary values.

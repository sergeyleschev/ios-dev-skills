# Task 3

Task: Write a method that takes an array of strings and returns a dictionary
that groups the strings by their first letter.

Solution:

```swift
func groupStringsByFirstLetter(_ strings: [String]) -> [Character: [String]] {
    var groupedStrings = [Character: [String]]()
    strings.forEach { string in
        let firstLetter = string.first ?? " "
        groupedStrings[firstLetter, default: []].append(string)
    }
    return groupedStrings
}
```

Differences from Middle 3 to Senior 1:

-   The ability to write code that is scalable and efficient, even for large
    data sets.
-   Experience with complex data structures and algorithms.
-   The ability to think critically and design elegant solutions to complex
    problems. ß

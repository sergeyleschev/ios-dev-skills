# Task 5

Task: Write a method that takes an array of strings and returns a new array with
all the strings that contain a given substring.

Solution:

```swift
func filterStringsBySubstring(_ strings: [String], substring: String) -> [String] {
    return strings.filter { $0.contains(substring) }
}
```

Differences from Middle 3 to Senior 1:

-   The ability to write concise and readable code that solves complex problems
    efficiently.
-   Knowledge of advanced Swift features and language constructs, and how to use
    them effectively.
-   The ability to think holistically about software design, including
    architecture, scalability, and maintainability.

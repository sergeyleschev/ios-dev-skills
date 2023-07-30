# Task 3

Task: Given a dictionary with string keys and integer values, write a function
to return the keys of the top three values in descending order.

Example: Input: ["apple": 5, "banana": 3, "orange": 7, "peach": 7] Output:
["orange", "peach", "apple"]

Solution:

```swift
func topThreeKeys(from dict: [String: Int]) -> [String] {
    let sortedTuples = dict.sorted { $0.value > $1.value }
    return Array(sortedTuples.prefix(3)).map { $0.key }
}
```

In this task, the main focus is on working with dictionaries and sorting them
based on values. The solution involves sorting the dictionary based on values,
taking the first three elements of the sorted array, and then mapping them to
their keys. By implementing this solution, the developer demonstrates their
understanding of basic dictionary operations and sorting.

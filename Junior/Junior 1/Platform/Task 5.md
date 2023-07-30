# Task 5

Task: Write a function that takes in two dictionaries of type
**`[String: Int]`** and returns a new dictionary that contains the key-value
pairs that are present in both dictionaries. If a key is present in both
dictionaries, the value in the returned dictionary should be the sum of the
values in both input dictionaries. If a key is only present in one of the
dictionaries, it should not be included in the returned dictionary.

Solution:

```swift
func combineDictionaries(dict1: [String: Int], dict2: [String: Int]) -> [String: Int] {
    var combinedDict = [String: Int]()

    for (key, value) in dict1 {
        if let otherValue = dict2[key] {
            combinedDict[key] = value + otherValue
        }
    }

    return combinedDict
}
```

Differences from the Junior 1 task:

This task involves working with two dictionaries instead of one, and combining
their key-value pairs based on whether they exist in both dictionaries. It
requires a deeper understanding of how to iterate over dictionaries and use
optional binding to safely access values.

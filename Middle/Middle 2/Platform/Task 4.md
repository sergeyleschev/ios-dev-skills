# Task 4

Task: Given a dictionary with key-value pairs of type **`[String: [String]]`**,
write a function that takes in the dictionary as input and returns a set
containing all the unique values from all the key-value pairs in the dictionary.

Solution:

```swift
func uniqueValues(from dictionary: [String: [String]]) -> Set<String> {
    var values = [String]()
    for valueArray in dictionary.values {
        values.append(contentsOf: valueArray)
    }
    return Set(values)
}
```

Differences from previous level:

-   This task requires the developer to extract all values from a nested
    dictionary of arrays, which requires more complex handling of data than
    previous tasks.
-   The solution also makes use of the **`append(contentsOf:)`** method to
    concatenate arrays, which is a more efficient way of appending multiple
    elements to an array than using a **`for`** loop.
-   The solution also returns a **`Set`** instead of an array, which
    demonstrates understanding of the appropriate data structure to use for a
    given problem.

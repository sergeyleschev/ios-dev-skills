# Task 2

Task: Write a function that sorts an array of strings in alphabetical order.

Solution:

```swift
func sortStringsAlphabetically(_ strings: [String]) -> [String] {
    return strings.sorted()
}
```

Explanation:

This function uses the **`sorted()`** method provided by Swift's standard
library to sort the array of strings in alphabetical order. The **`sorted()`**
method returns a new array that contains the elements of the original array
sorted in ascending order, in this case, in alphabetical order.

Example usage:

```swift
let unsortedStrings = ["Apple", "Banana", "Cherry", "Date"]
let sortedStrings = sortStringsAlphabetically(unsortedStrings)
print(sortedStrings) // Output: ["Apple", "Banana", "Cherry", "Date"]
```

Difference between Junior 1 and Junior 2:

The Junior 2 level developer's solution demonstrates a deeper understanding of
Swift's standard library and its methods. They use the **`sorted()`** method
instead of implementing their own sorting algorithm or using a more complex
algorithm like quicksort. Additionally, the Junior 2 developer's code follows
Swift's naming conventions by using a descriptive function name
**`sortStringsAlphabetically(_:)`** instead of a generic name like
**`sortArray(_:)`**. Finally, the Junior 2 developer's code is more concise as
they avoid unnecessary steps like declaring an empty array or using a for loop
to iterate over the array. Overall, the Junior 2 developer's solution is more
advanced and efficient than that of the Junior 1 developer.

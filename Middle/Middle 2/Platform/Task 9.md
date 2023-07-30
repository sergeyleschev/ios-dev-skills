# Task 9

Task: Create a function that takes an array of integers and returns a new array
with all duplicates removed. The function should also sort the array in
ascending order.

Solution:

```swift
func removeDuplicates(from numbers: [Int]) -> [Int] {
    let set = Set(numbers)
    let sorted = set.sorted()
    return sorted
}
```

Difference from Middle 1 level:

-   The use of Set to efficiently remove duplicates from an array.
-   The use of the **`sorted()`** method on a Set to sort the unique elements in
    ascending order.
-   The use of more complex functional programming concepts like **`Set`** and
    **`sorted()`** to achieve a solution that is both concise and efficient.

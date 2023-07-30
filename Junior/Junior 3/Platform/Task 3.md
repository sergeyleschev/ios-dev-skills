# Task 3

Task: Write a function that takes in an array of integers and returns the second
highest number in the array.

Solution:

```swift
func secondHighestNumber(from numbers: [Int]) -> Int? {
    guard numbers.count >= 2 else { return nil }
    let sortedNumbers = numbers.sorted(by: >)
    return sortedNumbers[1]
}
```

Differences from the previous level (Junior 2):

-   The solution uses the **`guard`** statement to check for the minimum length
    of the input array.
-   The solution sorts the array in descending order to get the second highest
    number.
-   The solution returns an optional value to handle the case where there are
    less than two elements in the array.

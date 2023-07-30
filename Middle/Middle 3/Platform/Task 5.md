# Task 5

Task: Given two arrays of integers, write a function to return an array
containing the common elements in both arrays, sorted in ascending order.

Solution:

```swift
func findCommonElements(_ array1: [Int], _ array2: [Int]) -> [Int] {
    var set1 = Set(array1)
    var commonElements = [Int]()
    for number in array2 {
        if set1.contains(number) {
            commonElements.append(number)
        }
    }
    return commonElements.sorted()
}
```

Differences from Middle 2 level:

-   The solution uses a Set data structure to optimize the search for common
    elements, which is a more advanced technique than just iterating over the
    arrays.
-   The function parameter names are more descriptive and clear, indicating
    attention to detail and best practices.
-   The function returns the common elements sorted, which shows an
    understanding of algorithmic complexity and efficiency.

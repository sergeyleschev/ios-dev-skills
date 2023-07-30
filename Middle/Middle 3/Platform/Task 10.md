# Task 10

Task: Write a function that takes two arrays of equatable elements and returns
an array of elements that are present in both input arrays.

Solution:

```swift
func commonElements<T: Equatable>(_ arr1: [T], _ arr2: [T]) -> [T] {
    var result = [T]()
    let set1 = Set(arr1)
    let set2 = Set(arr2)
    for element in set1 {
        if set2.contains(element) {
            result.append(element)
        }
    }
    return result
}
```

Differences from Middle 2 level:

-   The solution now requires knowledge of how to work with Equatable and
    Hashable protocols.
-   The use of sets to determine common elements allows for more efficient
    performance than comparing each element in both arrays.

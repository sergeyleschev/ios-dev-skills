# Task 10

Task:

Write a function that takes in an array of integers and returns a new array
containing only the unique elements of the original array in the order they
appear. Use a Set to keep track of seen elements.

Solution:

```swift
func uniqueElements(in array: [Int]) -> [Int] {
    var uniqueElements: [Int] = []
    var seenElements: Set<Int> = []

    for element in array {
        if !seenElements.contains(element) {
            uniqueElements.append(element)
            seenElements.insert(element)
        }
    }

    return uniqueElements
}
```

Difference from previous level:

At the previous level, the developer was able to loop over an array and check if
an element is contained in a set. At this level, the developer is able to create
a new array with only unique elements, using a combination of an empty array and
a set to keep track of seen elements. This demonstrates a stronger understanding
of data structures and algorithms.

# Task 4

Task: Write a method that takes an array of integers and returns the highest
product of any three numbers in the array.

Solution:

```swift
func highestProductOfThree(_ nums: [Int]) -> Int {
    guard nums.count >= 3 else {
        fatalError("Array must contain at least 3 integers.")
    }
    let sortedNums = nums.sorted()
    let lastIndex = sortedNums.count - 1
    let productOfLastThree = sortedNums[lastIndex] * sortedNums[lastIndex - 1] * sortedNums[lastIndex - 2]
    let productOfFirstTwoLastOne = sortedNums[lastIndex] * sortedNums[0] * sortedNums[1]
    return max(productOfLastThree, productOfFirstTwoLastOne)
}
```

Differences from Middle 3 to Senior 1:

-   The ability to analyze and optimize algorithms for better performance.
-   Knowledge of common data structures and algorithms, and how to use them
    effectively in code.
-   The ability to think creatively and come up with solutions to complex
    problems.

# Task 5

Task: Given an array of integers, write a function that finds all pairs of
integers whose sum is equal to a given target integer. The function should
return an array of tuples, where each tuple represents a pair of integers that
add up to the target.

Example:

```swift
let nums = [1, 3, 5, 7, 9, 11]
let target = 10

findPairs(in: nums, withSumEqualTo: target)

// Returns [(1, 9), (3, 7)]
```

Solution:

```swift
func findPairs(in nums: [Int], withSumEqualTo target: Int) -> [(Int, Int)] {
    var pairs: [(Int, Int)] = []
    var seenNumbers: Set<Int> = []

    for num in nums {
        let complement = target - num

        if seenNumbers.contains(complement) {
            pairs.append((num, complement))
        }

        seenNumbers.insert(num)
    }

    return pairs
}
```

In this task, we're building on the previous task by introducing the concept of
sets and using it to solve the problem. The key difference between this task and
the previous one is that we're now using a set to keep track of the numbers
we've seen so far, which allows us to quickly check whether a complement to the
current number has already been seen. This approach has a time complexity of
O(n), making it more efficient than the brute-force approach used in the
previous task.

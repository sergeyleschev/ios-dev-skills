# Task 4

Task: Write a function that takes in an array of strings and returns the
frequency of each word in the array as a dictionary.

Solution:

```swift
func wordFrequency(in array: [String]) -> [String: Int] {
    var frequency: [String: Int] = [:]
    for word in array {
        frequency[word, default: 0] += 1
    }
    return frequency
}
```

Explanation: This task requires the use of a dictionary to store the frequency
of each word in the given array. The function takes in an array of strings and
initializes an empty dictionary. Then, it iterates over each word in the array
and updates the frequency count in the dictionary accordingly. Finally, it
returns the dictionary containing the frequency of each word in the array.

The main difference between this task and the previous ones is that it requires
the developer to combine their knowledge of arrays, loops, and dictionaries to
solve a more complex problem. It also requires a better understanding of
dictionary methods such as **`default:`**. The interviewer should look for clean
and efficient code, as well as the ability to solve a more challenging problem.

# Task 4

Task: Write a function that takes an array of integers as input and returns a
dictionary where the keys are the unique integers in the array and the values
are the number of times each integer appears in the array.

Solution:

```swift
func countOccurrences(_ array: [Int]) -> [Int: Int] {
    var occurrences: [Int: Int] = [:]
    for number in array {
        if let count = occurrences[number] {
            occurrences[number] = count + 1
        } else {
            occurrences[number] = 1
        }
    }
    return occurrences
}
```

Explanation: This task requires the use of an array and a dictionary. The
function takes an array of integers as input and initializes an empty dictionary
to store the number of occurrences of each integer. It then iterates through the
array, checking if the current number is already a key in the dictionary. If it
is, the count value is incremented by 1. If it is not, a new key-value pair is
added to the dictionary with a count of 1. Finally, the dictionary of
occurrences is returned.

The main difference between this task and the previous one is that it requires
the use of a dictionary to store the counts of the integers in the input array,
whereas the previous task only required the use of an array. This task also
requires more complex logic to iterate through the array and update the
dictionary, making it a suitable step up for a junior developer.

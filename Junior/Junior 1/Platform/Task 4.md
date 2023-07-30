# Task 4

Task: Given an array of integers, find the number of unique elements in the
array using a dictionary.

Solution:

```swift
let array = [1, 2, 3, 2, 4, 5, 1, 3, 6, 7, 7, 8, 9]
var dictionary = [Int: Bool]()
var count = 0

for element in array {
    if dictionary[element] == nil {
        dictionary[element] = true
        count += 1
    }
}

print(count)
```

Explanation:

This solution uses a dictionary to keep track of the unique elements in the
array. We iterate through the array and check if the element is already in the
dictionary. If it is not, we add the element to the dictionary with a boolean
value of **`true`**, indicating that the element is unique. We also increment a
**`count`** variable to keep track of the number of unique elements we have
encountered so far. Finally, we print out the **`count`** variable.

This task is a step up from the previous task for Junior 1 as it requires the
use of a dictionary, which is not covered in the Junior 1 task. It also involves
checking for and adding elements to the dictionary, which is a more complex use
case compared to just retrieving elements from the dictionary.

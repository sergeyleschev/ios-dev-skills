# Task 2

Task: Write a function that takes in an array of integers and returns the sum of
all the even numbers in the array. If there are no even numbers in the array,
the function should return 0.

Example Input: [1, 2, 3, 4, 5, 6]

Example Output: 12 (sum of 2, 4, and 6)

Solution:

```swift
func sumOfEvenNumbers(in array: [Int]) -> Int {
    var sum = 0
    for number in array {
        if number % 2 == 0 {
            sum += number
        }
    }
    return sum
}
```

This solution defines a function called **`sumOfEvenNumbers(in:)`** that takes
in an array of integers as a parameter. The function initializes a **`sum`**
variable to 0 and then iterates over each number in the array. If the number is
even (determined by checking if it's divisible by 2 with no remainder), it's
added to the **`sum`**. Finally, the function returns the sum of all even
numbers in the array. If there are no even numbers in the array, the function
will return 0.

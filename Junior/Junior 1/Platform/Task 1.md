# Task 1

Task: Given an array of integers, write a function that returns the sum of all
even numbers in the array.

Solution:

```swift
func sumOfEvenNumbers(in array: [Int]) -> Int {
    var sum = 0
    for num in array {
        if num % 2 == 0 {
            sum += num
        }
    }
    return sum
}
```

Explanation:

-   The function **`sumOfEvenNumbers(in:)`** takes an array of integers as input
    and returns an integer which is the sum of all even numbers in the array.
-   We initialize a variable **`sum`** to 0 to keep track of the sum of even
    numbers.
-   We loop through each number in the array using a **`for`** loop.
-   Inside the loop, we check if the number is even by checking if the remainder
    of the number divided by 2 is 0. If the number is even, we add it to the
    **`sum`**.
-   After we have looped through all the numbers in the array, we return the
    **`sum`**.

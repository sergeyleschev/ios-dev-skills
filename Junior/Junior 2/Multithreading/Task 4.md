# Task 4

Task: Given an array of integers, write a function that finds the sum of all the
even numbers in the array. Make the function asynchronous using Grand Central
Dispatch (GCD) and perform the calculation on a background thread. Once the
calculation is complete, update the user interface with the result on the main
thread.

Solution:

```swift
func sumOfEvenNumbers(_ numbers: [Int], completion: @escaping (Int) -> Void) {
    DispatchQueue.global().async {
        var sum = 0
        for number in numbers {
            if number % 2 == 0 {
                sum += number
            }
        }
        DispatchQueue.main.async {
            completion(sum)
        }
    }
}
```

Differences indicating the development of the developer to the level of Junior
2:

-   Use of GCD to perform the calculation on a background thread
-   Separation of calculation logic from UI update logic using a completion
    closure
-   Use of **`@escaping`** closure to indicate that the closure may be called
    asynchronously after the function returns
-   Use of **`DispatchQueue.main.async`** to update the user interface on the
    main thread.

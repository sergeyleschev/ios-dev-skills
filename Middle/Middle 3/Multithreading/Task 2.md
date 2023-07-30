# Task 2

Task: Write a function that calculates the sum of a large array of integers on a
background thread and displays the result on the main thread. However, the
calculation should be cancelled after 10 seconds if it takes too long. Use GCD
to perform the background task and ensure thread safety.

Solution:

```swift
func calculateSumInBackground(_ array: [Int], completion: @escaping (Int?) -> Void) {
    // Create a background queue
    let backgroundQueue = DispatchQueue.global(qos: .background)

    // Calculate sum on background thread
    var sum = 0
    var cancelled = false
    backgroundQueue.async {
        for num in array {
            if cancelled {
                completion(nil)
                return
            }
            sum += num
        }

        // Display sum on main thread
        DispatchQueue.main.async {
            completion(sum)
        }
    }

    // Cancel calculation after 10 seconds if it takes too long
    backgroundQueue.asyncAfter(deadline: .now() + 10) {
        cancelled = true
    }
}
```

Differences from the previous level (Middle 2):

-   The solution involves using GCD to perform the background task instead of
    just creating a background thread
-   The solution includes cancelling the calculation after 10 seconds if it
    takes too long
-   The solution handles thread safety by ensuring that the completion block
    happens on the main thread.

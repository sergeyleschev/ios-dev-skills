# Task 3

Task:

You are given an array of integers. Write a code snippet that sorts the array in
ascending order using a background thread and then updates the UI with the
sorted results on the main thread.

Solution:

To sort an array of integers in ascending order and update the UI with the
sorted results, we can use GCD to perform the sorting in a background thread and
then switch back to the main thread to update the UI. Here's an example code
snippet that demonstrates how to achieve this:

```swift
DispatchQueue.global(qos: .background).async {
    // Sort the array in ascending order
    let sortedArray = array.sorted()

    DispatchQueue.main.async {
        // Update the UI with the sorted results
        // For example, update a table view or collection view with the sorted data
    }
}
```

In this code, we use the **`DispatchQueue.global(qos: .background).async`**
method to execute the sorting in a background thread with a lower quality of
service (QoS) level. This ensures that the sorting does not block the main
thread and cause the UI to freeze.

Once the sorting is complete, we use **`DispatchQueue.main.async`** to switch
back to the main thread and update the UI with the sorted results. This ensures
that the UI updates are performed on the main thread, which is necessary to
avoid synchronization issues.

Difference from the Middle 1 level:

The code snippet above shows an understanding of how to use GCD to sort an array
of integers in a background thread and update the UI with the sorted results on
the main thread. This demonstrates an intermediate level of proficiency with
multithreading concepts and a better understanding of how to use GCD to perform
complex operations in the background without affecting the UI responsiveness.

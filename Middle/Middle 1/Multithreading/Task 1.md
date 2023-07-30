# Task 1

Task: You are working on a project where performance is crucial. You have
noticed that using **`asyncAfter`** for scheduling tasks is causing some
performance issues. Your task is to identify the problem and suggest an
alternative approach to schedule tasks.

Solution: Using **`asyncAfter`** for scheduling tasks is not an efficient
approach as it creates a new thread and can potentially block the main thread,
leading to performance issues. Instead, we can use **`DispatchQueue`** to
schedule tasks on a background thread and use **`DispatchGroup`** to synchronize
tasks.

Here is an example of scheduling tasks using **`DispatchQueue`** and
**`DispatchGroup`**:

```swift
let dispatchQueue = DispatchQueue(label: "com.example.myqueue", attributes: .concurrent)
let dispatchGroup = DispatchGroup()

dispatchQueue.async(group: dispatchGroup) {
    // Perform task 1
}

dispatchQueue.async(group: dispatchGroup) {
    // Perform task 2
}

dispatchQueue.async(group: dispatchGroup) {
    // Perform task 3
}

dispatchGroup.notify(queue: DispatchQueue.main) {
    // All tasks are completed
}
```

In this example, we create a **`DispatchQueue`** with a unique label to avoid
conflicts with other queues in the system. We then create a **`DispatchGroup`**
to synchronize tasks.

We use the **`async`** method of the **`DispatchQueue`** to schedule tasks and
pass the **`DispatchGroup`** instance as a parameter to group tasks together.

Finally, we use the **`notify`** method of the **`DispatchGroup`** to execute a
completion block once all tasks are completed. The completion block is executed
on the main thread, allowing us to update the user interface if needed.

The key difference in this solution compared to the previous level (Junior 3) is
the use of **`DispatchQueue`** and **`DispatchGroup`** instead of
**`asyncAfter`** and **`@synchronized`**. This shows that the developer has
moved on from basic multithreading concepts and is now familiar with more
advanced techniques to improve performance.

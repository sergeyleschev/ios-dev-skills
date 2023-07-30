# Task 3

Task:

You have a long-running task that needs to be performed in the background
without blocking the main thread. This task needs to be performed once every
minute. Write a solution that achieves this requirement and handles any possible
concurrency issues.

Solution:

To perform a long-running task every minute without blocking the main thread, we
can use a background thread and a timer. Here's a possible solution:

```swift
let queue = DispatchQueue(label: "com.example.myqueue", qos: .background, attributes: .concurrent)

let timer = DispatchSource.makeTimerSource(queue: queue)
timer.schedule(deadline: .now(), repeating: .minutes(1))

timer.setEventHandler {
    // Perform the long-running task here
}

timer.resume()
```

This code creates a **`DispatchQueue`** with a background quality of service and
sets up a timer that fires every minute. The timer is configured to call a block
of code that performs the long-running task. The **`timer.resume()`** call
starts the timer.

To handle any possible concurrency issues, we're using a concurrent queue and
ensuring that the timer's event handler is called on the same background queue.
This ensures that the long-running task is executed serially and doesn't
interfere with other operations that might be running concurrently on the same
queue.

One key difference from the junior level solutions is the use of a
**`DispatchQueue`** with a concurrent quality of service, which allows for
multiple tasks to run simultaneously. Additionally, the use of
**`DispatchSource.makeTimerSource`** enables more fine-grained control over the
scheduling of the long-running task. Overall, this solution demonstrates a more
advanced understanding of concurrency and the Grand Central Dispatch framework.

# Task 5

Task: You are given a function **`fetchData(completion:)`** that fetches some
data from a network API asynchronously and calls the completion handler when
it's done. You need to call this function 5 times concurrently and wait for all
5 calls to finish before proceeding to the next step.

Solution:

```swift
let group = DispatchGroup()

for _ in 0..<5 {
    group.enter()
    fetchData { data in
        // Handle the fetched data
        group.leave()
    }
}

group.wait()
// All 5 fetch calls have finished at this point
```

In this task, the developer needs to be familiar with using **`DispatchGroup`**
to wait for multiple async tasks to finish, as well as understanding how to call
a function asynchronously multiple times concurrently. This task also tests the
developer's ability to handle completion handlers and asynchronous programming
in general. To indicate the development from middle 1 to middle 2, the developer
should be able to handle more complex situations where multiple async tasks need
to be synchronized or where more advanced multithreading techniques are needed.

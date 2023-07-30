# Task 2

Task: You are working on an app that has a complex data structure that needs to
be accessed by multiple threads simultaneously. One of the threads is
responsible for updating the data, while the other threads are responsible for
reading the data. Occasionally, you notice that the app crashes when accessing
the data structure, and you suspect that this may be due to a race condition.

Your task is to identify the potential race condition in the code and suggest a
solution to prevent it.

Code:

```swift
class DataStore {
    var data: [Int] = []
    let queue = DispatchQueue(label: "com.example.datastore")

    func updateData(newData: Int) {
        queue.async {
            self.data.append(newData)
        }
    }

    func readData() -> [Int] {
        var result: [Int] = []
        queue.sync {
            result = self.data
        }
        return result
    }
}
```

Solution:

The potential race condition in the code is caused by the fact that the
**`updateData()`** and **`readData()`** methods are accessing the same data
structure (**`self.data`**) without any synchronization mechanism. This can lead
to situations where multiple threads are trying to access the data structure
simultaneously, leading to unpredictable results, including crashes.

To prevent this race condition, one solution is to use a concurrent dispatch
queue instead of a serial dispatch queue for accessing the data structure. This
will allow multiple threads to read the data simultaneously while ensuring that
updates to the data structure are serialized.

Here's an updated implementation that uses a concurrent dispatch queue:

```swift
class DataStore {
    private var data: [Int] = []
    private let queue = DispatchQueue(label: "com.example.datastore", attributes: .concurrent)

    func updateData(newData: Int) {
        queue.async(flags: .barrier) {
            self.data.append(newData)
        }
    }

    func readData() -> [Int] {
        var result: [Int] = []
        queue.sync {
            result = self.data
        }
        return result
    }
}

```

The **`updateData()`** method now uses the **`.barrier`** flag to specify that
it should be executed as a barrier block, which ensures that all previously
enqueued blocks are completed before executing the barrier block. This means
that while the update is being performed, all other read and write operations
will be blocked, ensuring that the data structure is accessed in a synchronized
manner.

# Task 2

Task: Given an array of custom objects, implement a function to sort them based
on a certain property of the object. The sorting should be done in a memory
efficient way to avoid excessive memory usage.

Solution:

To sort an array of custom objects based on a property in a memory-efficient
way, we can use the **`sort`** function along with a closure to specify the
sorting logic. Here's an example implementation:

```swift
struct CustomObject {
    var id: Int
    var name: String
    var value: Double
}

let objects = [CustomObject(id: 1, name: "Object 1", value: 3.5),
               CustomObject(id: 2, name: "Object 2", value: 2.7),
               CustomObject(id: 3, name: "Object 3", value: 5.0),
               CustomObject(id: 4, name: "Object 4", value: 1.2)]

// Sort objects based on the 'value' property in ascending order
objects.sort { $0.value < $1.value }

// Sort objects based on the 'id' property in descending order
objects.sort { $0.id > $1.id }
```

One difference between this task and the previous ones is that this task
requires sorting an array of custom objects based on a certain property, rather
than just identifying and fixing memory leaks. The solution demonstrates how to
use the **`sort`** function with a closure to specify the sorting logic. In
addition, the prompt mentions the importance of doing this sorting in a
memory-efficient way to avoid excessive memory usage, which can be achieved by
using the **`sort`** function instead of creating a new array or collection.

# Task 1

Task: Create a function that takes in an array of custom objects and returns a
new array of the same objects with a property **`isActive`** set to **`false`**
if the original object's property **`expirationDate`** is less than the current
date.

Solution:

```swift
struct CustomObject {
    let id: Int
    let expirationDate: Date
    var isActive: Bool
}

func updateObjectsExpirationStatus(_ objects: [CustomObject]) -> [CustomObject] {
    var updatedObjects = objects
    let currentDate = Date()

    for index in 0..<updatedObjects.count {
        if updatedObjects[index].expirationDate < currentDate {
            updatedObjects[index].isActive = false
        }
    }

    return updatedObjects
}
```

The above function takes in an array of **`CustomObject`** structs and iterates
over each object checking if its **`expirationDate`** property is less than the
current date. If so, it sets the object's **`isActive`** property to
**`false`**. The function returns a new array of the updated objects.

Difference from Senior 1 to Senior 2: At the Senior 2 level, the developer
should have a deeper understanding of memory management, and should be able to
use more advanced techniques such as weak and unowned references to prevent
retain cycles and memory leaks. Additionally, they should be familiar with
instruments and profiling tools to identify and fix performance and memory
issues.

# Task 1

Task: Implement a method that takes an array of objects as a parameter and
returns a new array with only the objects that are not being retained by any
other objects in the system.

Solution:

```swift
func findUnretainedObjects(in objects: [AnyObject]) -> [AnyObject] {
    let unretainedObjects = objects.filter { object in
        let count = CFGetRetainCount(object)
        return count == 1
    }
    return unretainedObjects
}
```

Differences from Middle 2 level:

-   The developer now uses **`CFGetRetainCount`** to accurately determine the
    retain count of each object.
-   The method takes an array of **`AnyObject`** instead of a specific object
    type to demonstrate a deeper understanding of memory management.
-   The method returns an array of **`AnyObject`** instead of a specific object
    type to demonstrate a deeper understanding of memory management.

# Task 6

Task: Write a function that takes in an array of custom objects and removes any
duplicates based on a specific property of the object. The function should be
generic and work for any object that conforms to the Equatable and Hashable
protocols.

Solution:

```swift
func removeDuplicates<T: Equatable & Hashable>(from array: [T], by keyPath: KeyPath<T, Any>) -> [T] {
    var set = Set<AnyHashable>()
    var result = [T]()

    for object in array {
        let value = object[keyPath: keyPath]
        if !set.contains(value) {
            set.insert(value)
            result.append(object)
        }
    }

    return result
}
```

The main difference between this task and the previous ones is that it requires
knowledge of value and reference types, as well as the Equatable and Hashable
protocols. The function takes in an array of custom objects and uses a keyPath
to access a specific property of the object for comparison. It then uses a Set
to remove any duplicates and returns the unique objects as an array. This task
tests the developer's ability to work with custom objects and understand how to
compare them based on specific properties.

# Task 1

Task: Write a function in Swift that receives an array of objects with a
property "name" and returns a new array with only the names of the objects that
start with the letter "A". Make sure to avoid any memory leaks in the
implementation.

Solution:

```swift
func getNamesStartingWithA(from objects: [MyObject]) -> [String] {
    var result = [String]()
    for object in objects {
        if object.name.hasPrefix("A") {
            result.append(object.name)
        }
    }
    return result
}
```

Differences from Junior 1 level:

1. The developer is able to write a more complex function that performs a
   specific task.
2. The developer is able to use Swift's **`hasPrefix`** function to check for a
   specific character at the beginning of a string, showing a deeper
   understanding of Swift's built-in functions.
3. The developer has a better understanding of memory management and avoids any
   memory leaks in the implementation.

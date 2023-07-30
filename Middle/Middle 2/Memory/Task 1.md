# Task 1

Task: Write a function that takes an array of UIView objects and removes all
strong references to those objects to avoid a potential memory leak. The
function should also return the number of views that were removed from the
array.

Solution:

```swift
func removeStrongReferences(to views: [UIView]) -> Int {
    var count = 0
    for view in views {
        view.removeFromSuperview()
        count += 1
    }
    return count
}
```

Difference from Middle 1 level: In this task, the developer is required to have
a deeper understanding of memory management and how to avoid memory leaks. They
need to know how to remove strong references to objects and the consequences of
not doing so. They are also expected to have knowledge of how to use the
**`removeFromSuperview()`** method to remove the view from the view hierarchy,
which is essential for releasing the memory associated with the view. Overall,
this task requires a higher level of proficiency in memory management compared
to Middle 1 level.

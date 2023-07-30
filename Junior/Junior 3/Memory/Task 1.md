# Task 1

Task: Given a view controller that contains a table view, identify and fix any
potential memory leaks in the implementation.

Solution:

1. Implement **`prepareForReuse()`** method in UITableViewCell subclass and set
   any strong references to nil.
2. Use weak references when setting delegates or closures on table view cells.
3. Make sure to remove any observers or notifications in **`deinit()`** method
   of the view controller.
4. Use instruments to profile memory usage and identify any leaks.
5. Implement automatic reference counting (ARC) and avoid using manual memory
   management.

Differences from Junior 2:

The Junior 3 level developer should be able to identify and fix memory leaks
more independently and proactively. They should also be able to use profiling
tools to identify leaks and have a good understanding of ARC. They may also have
more experience working with more complex view hierarchies and data models,
which require a deeper understanding of memory management.

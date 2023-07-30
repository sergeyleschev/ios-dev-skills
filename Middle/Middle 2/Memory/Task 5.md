# Task 5

Task:

You have been given an existing project with multiple view controllers, and you
are tasked with identifying and fixing any memory leaks present in the code. One
of the view controllers in the project is presenting a modal view controller,
but when the modal is dismissed, the memory usage of the app continues to
increase significantly.

Solution:

1. Check for strong reference cycles: Look for any objects that have a strong
   reference to each other and make sure to break those references if they are
   not necessary. Use tools like Xcode's Memory Graph Debugger or Instruments to
   identify these cycles.
2. Check for unowned or weak references: Use unowned or weak references for
   objects that may not exist for the entire lifecycle of the app. This can help
   to prevent memory leaks.
3. Implement lazy loading: Lazy loading is the technique of loading an object
   only when it is needed, rather than loading it when the app starts up. This
   can help to prevent unnecessary memory usage.
4. Deallocate objects when they are no longer needed: Make sure to remove any
   observers, delegates, or listeners when an object is no longer needed. This
   will ensure that the object is deallocated properly.
5. Use autorelease pools: Autorelease pools can help to manage memory usage by
   releasing objects when they are no longer needed. Use them for any code that
   creates a lot of temporary objects.

Differences indicating development from Middle 1 to Middle 2:

-   Better understanding and implementation of the above techniques.
-   Familiarity with advanced debugging tools and techniques to identify and fix
    memory leaks.
-   Ability to analyze and optimize memory usage of a complex project with
    multiple view controllers.

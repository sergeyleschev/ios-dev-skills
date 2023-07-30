# Task 2

Task: You are working on an app that uses Core Data to manage its data
persistence. You have noticed that the app is experiencing performance issues
and you suspect that there may be memory leaks in your Core Data implementation.
Your task is to identify and fix any memory leaks in your Core Data
implementation.

Solution: One way to avoid memory leaks in Core Data is to make sure that you
are properly managing the lifecycle of your managed objects. Here are some steps
you can take to fix any memory leaks:

1. Use autorelease pools: When you create a managed object context or fetch
   request, wrap it in an autorelease pool to ensure that any autoreleased
   objects are released as soon as possible.
2. Use weak references: When passing managed objects between view controllers or
   other objects, use weak references to avoid creating strong reference cycles.
3. Fetch only what you need: When fetching data from Core Data, use predicates
   to filter the results to only include the data you actually need.
4. Dispose of unused objects: When you are finished using a managed object,
   dispose of it as soon as possible by calling the **`deleteObject(_:)`**
   method on its managed object context.

By implementing these strategies, you can help ensure that your Core Data
implementation is free of memory leaks and that your app performs well. As a
Junior 3 developer, you should also be able to identify potential memory leaks
in your code before they become a problem and proactively take steps to avoid
them.

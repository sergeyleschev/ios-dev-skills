# Task 3

Task: You are working on an iOS app that fetches a large amount of data from a
server and displays it in a table view. You have noticed that the app is
consuming a lot of memory and is prone to crashing due to memory issues. Your
task is to identify the memory issues and fix them to ensure that the app runs
smoothly.

Solution: The issue with the app is most likely due to the large amount of data
being fetched and loaded into memory at once. One way to fix this is to
implement pagination, so that only a small subset of the data is loaded into
memory at a time.

Another approach is to make use of caching techniques such as NSCache or
NSURLCache, which can be used to store frequently accessed data in memory or on
disk respectively.

In addition to these techniques, it's also important to make sure that any
unused objects are released from memory as soon as possible. This can be done by
setting objects to nil when they are no longer needed or by making use of weak
or unowned references when working with object graphs.

The difference between a Senior 1 and a Senior 2 developer in this scenario is
that a Senior 2 developer would have a more advanced understanding of memory
management techniques, including advanced caching strategies, and would be able
to identify and resolve memory issues more quickly and efficiently. They would
also have a strong understanding of how to optimize memory usage in complex
applications with large data sets.

# Task 4

Task: You're working on an iOS app that heavily uses Core Data for data storage.
A user reports that the app is using a lot of memory and sometimes crashes.
After investigating, you find that the app is leaking memory when creating new
managed objects. Write a brief explanation of what could be causing the memory
leak and how you would go about fixing it.

Solution: The memory leak could be caused by retaining managed objects for too
long, leading to an accumulation of objects in memory. To fix the leak, we can
use autorelease pools to ensure that objects are released as soon as they are no
longer needed. We can also implement caching and lazy loading mechanisms to
reduce the number of managed objects that are created at once. Finally, we can
use tools like Instruments to analyze memory usage and identify any additional
areas of the app that might be leaking memory.

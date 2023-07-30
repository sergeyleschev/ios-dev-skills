# Task 5

Please provide a brief explanation of why some iOS apps can't use Swift Package
Manager (SPM), but Carthage is still an option for managing dependencies.

Answer:

SPM is a dependency manager for Swift that was introduced in Xcode 11. It's a
great tool for managing dependencies, but it has some limitations. For example,
it only supports iOS 8 and above, which means that if your app has a minimum
target below iOS 8, you can't use SPM. Another limitation of SPM is that it only
works with packages that are written in Swift.

Carthage, on the other hand, is a dependency manager that supports both Swift
and Objective-C packages. It also doesn't have the same minimum target
requirements as SPM, so it can be used for apps that have a minimum target below
iOS 8. Carthage also has the advantage of being able to build frameworks that
can be shared between multiple targets.

Differences between Middle 1 and Junior 3 level:

At the Middle 1 level, the developer should be able to not only explain the
limitations of different dependency managers but also understand the trade-offs
between them. They should be able to choose the right tool for the job and know
when to use each one. Additionally, they should have experience working with
multiple dependencies and be able to handle any conflicts or issues that arise.
The developer should also be comfortable with integrating third-party libraries
into their codebase and understanding the implications of doing so.

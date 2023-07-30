# Task 5

Task: Implement a dependency injection container in Swift

Instructions:

You are tasked with implementing a simple dependency injection container in
Swift that can be used to manage dependencies in a medium-sized iOS application.
The container should allow for the registration of dependencies and their
associated factories, and should provide a mechanism for resolving these
dependencies when needed.

Write a class called **`DependencyContainer`** that provides the following
methods:

-   **`register<T>(factory: @escaping () -> T)`** : Registers a factory closure
    for the type **`T`**.
-   **`resolve<T>() -> T`** : Resolves an instance of type **`T`** using its
    associated factory closure.

The container should also support registering dependencies as singletons,
meaning that the same instance will be returned every time it is resolved.

Additionally, provide a short explanation of why using a dependency injection
container can be beneficial in iOS development.

Note: You can assume that the factories are thread-safe and that there are no
circular dependencies.

Example usage:

```swift
let container = DependencyContainer()
container.register(factory: { MyService() })
let myService: MyService = container.resolve()
```

Differences from previous level (Middle 2):

-   This task requires the developer to have a deeper understanding of
    dependency injection and how it can be implemented in Swift.
-   The developer should be familiar with closures and their usage in Swift.
-   The developer should be able to write code that is thread-safe and can
    handle singleton instances.

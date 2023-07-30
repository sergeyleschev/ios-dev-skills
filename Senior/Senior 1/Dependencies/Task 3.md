# Task 3

Task: Implement a simple dependency injection container in Swift.

You are building a new iOS app and you need to manage dependencies between
different components of your app. You decide to implement a simple dependency
injection container to handle this.

Your container should have the following features:

1. Registering dependencies: The container should allow you to register
   dependencies with it. For example, if you have a class **`MyClass`** that
   depends on **`MyDependency`**, you should be able to register
   **`MyDependency`** with the container.
2. Resolving dependencies: The container should allow you to resolve
   dependencies. For example, if you have a class **`MyClass`** that depends on
   **`MyDependency`**, you should be able to ask the container to give you an
   instance of **`MyClass`** and the container should automatically provide an
   instance of **`MyDependency`** to **`MyClass`**.
3. Singletons: The container should allow you to register dependencies as
   singletons. This means that the container should only create one instance of
   the dependency and return that same instance every time the dependency is
   requested.

Your implementation should demonstrate your understanding of dependency
injection and the purpose and benefits of a DI container. It should be
well-structured and easy to understand.

# Task 2

Task: You are working on a team project and have been tasked with resolving a
merge conflict that has arisen in your codebase. The conflict is in a file
called **`ViewController.swift`** and the conflicting code is as follows:

```swift
<<<<<<< HEAD
func doSomething() {
    print("Function A")
}
=======
func doSomething() {
    print("Function B")
}
>>>>>>> feature-branch
```

Please resolve the conflict by keeping both changes and adding a new function
that prints "Function C".

Solution:

```swift
func doSomething() {
    print("Function A")
    print("Function B")
    print("Function C")
}
```

Explanation:

This task requires the developer to demonstrate their ability to resolve a merge
conflict using Git. The conflicting code includes two versions of a function,
with different implementations. The solution is to keep both changes by merging
them together and adding a new function that prints "Function C". This solution
shows the ability of the developer to use Git for code integration and conflict
resolution.

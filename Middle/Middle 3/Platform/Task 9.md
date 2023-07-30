# Task 9

Task:

Create a custom struct named **`Person`** with properties for **`name`**
(String), **`age`** (Int), and **`email`** (String). Implement **`Equatable`**
and **`Hashable`** protocols for the **`Person`** struct.

Then create a function named **`uniquePeople`** that takes an array of
**`Person`** objects as an argument and returns an array containing only the
unique **`Person`** objects, i.e., without any duplicates.

Solution:

```swift
struct Person: Equatable, Hashable {
    let name: String
    let age: Int
    let email: String
}

func uniquePeople(_ people: [Person]) -> [Person] {
    var uniquePeople = Set<Person>()
    for person in people {
        uniquePeople.insert(person)
    }
    return Array(uniquePeople)
}
```

Differences from Middle Level 2 to Middle Level 3:

1. Understanding Value vs Reference Types: The Middle Level 3 developer
   understands the difference between value and reference types and how they are
   passed around in Swift. They can easily identify when to use one or the other
   and the implications of doing so.
2. Knowledge of Equatable and Hashable Protocols: The Middle Level 3 developer
   has a solid understanding of the Equatable and Hashable protocols and how
   they can be used to compare and store objects in collections such as Sets and
   Dictionaries.
3. Problem-Solving and Efficiency: The Middle Level 3 developer has honed their
   problem-solving skills and can come up with efficient solutions to problems
   in a shorter amount of time. They are able to quickly identify the best data
   structures and algorithms to use to solve a given problem.

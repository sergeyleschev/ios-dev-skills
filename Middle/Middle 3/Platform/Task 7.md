# Task 7

Task: Given an array of **`Person`** structs, remove duplicates based on their
**`id`** property and return a new array with unique **`Person`** instances. The
**`Person`** struct has a **`name`** and an **`id`** property, and conforms to
the **`Equatable`** and **`Hashable`** protocols.

```swift
struct Person: Equatable, Hashable {
    let name: String
    let id: Int
}

func removeDuplicates(_ persons: [Person]) -> [Person] {
    var uniquePersons: [Person] = []
    var idSet: Set<Int> = []

    for person in persons {
        if !idSet.contains(person.id) {
            uniquePersons.append(person)
            idSet.insert(person.id)
        }
    }

    return uniquePersons
}
```

Differences from the previous Middle level task:

-   Requires knowledge of value/reference types and how to use them to compare
    and store data efficiently.
-   Requires knowledge of the **`Equatable`** and **`Hashable`** protocols and
    how to conform to them for custom types.
-   Requires knowledge of using a **`Set`** to efficiently check for duplicates
    in a collection.
-   Requires a more complex solution involving multiple data structures to
    efficiently remove duplicates.

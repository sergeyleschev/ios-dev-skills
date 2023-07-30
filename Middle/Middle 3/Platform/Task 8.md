# Task 8

Task: Create a function that takes an array of objects and returns a set of
unique objects based on a specific property of the objects.

Solution:

```swift
struct Person {
    let id: Int
    let name: String
}

func uniquePeople(from people: [Person]) -> Set<Person> {
    return Set(people)
}

let people = [Person(id: 1, name: "Alice"), Person(id: 2, name: "Bob"), Person(id: 1, name: "Charlie")]
let uniquePeople = uniquePeople(from: people)
print(uniquePeople) // [{id 1, name "Alice"}, {id 2, name "Bob"}]
```

In this solution, we're using a **`Set`** to get unique values of **`Person`**
objects. The **`Person`** struct is able to be used in a **`Set`** because it
conforms to the **`Hashable`** protocol, which requires a **`hashValue`**
property to be implemented based on the values of its properties. We're also
using the default implementation of **`Equatable`** for **`Person`**, which
compares equality based on all of its properties.

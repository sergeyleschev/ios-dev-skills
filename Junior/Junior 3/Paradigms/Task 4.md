# Task 4

Task: Implement a protocol with associated type and use it in a generic function
that returns an array of objects conforming to the protocol.

Solution:

```swift
protocol Identifiable {
    associatedtype Identifier: Hashable
    var id: Identifier { get }
}

struct User: Identifiable {
    typealias Identifier = String
    let id: Identifier
    let name: String
}

struct Post: Identifiable {
    typealias Identifier = Int
    let id: Identifier
    let title: String
}

func getObjects<T: Identifiable>(withIds ids: [T.Identifier], from objects: [T]) -> [T] {
    return objects.filter { ids.contains($0.id) }
}

let users = [User(id: "1", name: "John"), User(id: "2", name: "Jane"), User(id: "3", name: "Bob")]
let posts = [Post(id: 1, title: "Hello World"), Post(id: 2, title: "Swift is awesome")]

let selectedUsers = getObjects(withIds: ["1", "3"], from: users)
print(selectedUsers) // Output: [User(id: "1", name: "John"), User(id: "3", name: "Bob")]

let selectedPosts = getObjects(withIds: [2], from: posts)
print(selectedPosts) // Output: [Post(id: 2, title: "Swift is awesome")]
```

In this task, we introduced a protocol with an associated type called
**`Identifiable`**. We defined two structs, **`User`** and **`Post`**, that
conform to this protocol. We then implemented a generic function called
**`getObjects`** that takes an array of identifiers and an array of objects and
returns an array of objects that have an ID in the list of identifiers. The
function uses the **`filter`** method to filter out the objects with matching
IDs. The **`getObjects`** function takes a generic type parameter **`T`** that
conforms to the **`Identifiable`** protocol, which allows us to use it with both
**`User`** and **`Post`** types. Finally, we tested the function by passing in
arrays of **`User`** and **`Post`** objects and verifying that it returns the
correct subset of objects.

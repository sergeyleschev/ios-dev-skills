# Task 2

Task: Write a class called **`UserManager`** that manages a list of users. The
class should have a method called **`addUser`** that takes in a **`User`**
object and adds it to the list of users. The class should also have a method
called **`getUser`** that takes in a username as a parameter and returns the
corresponding **`User`** object if it exists in the list. If the user does not
exist, the method should return **`nil`**.

Solution:

```swift
class UserManager {
    var users: [User] = []

    func addUser(_ user: User) {
        users.append(user)
    }

    func getUser(username: String) -> User? {
        return users.first(where: { $0.username == username })
    }
}

class User {
    let username: String
    let password: String

    init(username: String, password: String) {
        self.username = username
        self.password = password
    }
}

// Example usage
let userManager = UserManager()
let user1 = User(username: "johndoe", password: "password123")
let user2 = User(username: "janedoe", password: "qwerty")
userManager.addUser(user1)
userManager.addUser(user2)
let foundUser = userManager.getUser(username: "johndoe")
print(foundUser?.username) // Output: "johndoe"
```

Differences from Junior 2 level:

-   The Junior 3 level task requires the candidate to demonstrate an
    understanding of class composition and data structures. The
    **`UserManager`** class manages a list of **`User`** objects, which requires
    the use of an array data structure to store and retrieve data.
-   The solution also uses higher-order functions like **`first(where:)`** to
    search through the list of users based on a predicate function.
-   Additionally, the solution demonstrates good code organization by separating
    the **`User`** and **`UserManager`** classes into separate files or code
    blocks.

# Task 1

Task: Write a method that takes an array of dictionaries, each containing a name
and age, and returns a new array of the names sorted alphabetically.

Solution:

```swift
func sortNamesByAlphabeticalOrder(_ people: [[String: Any]]) -> [String] {
    let sortedPeople = people.sorted { (person1, person2) -> Bool in
        guard let name1 = person1["name"] as? String, let name2 = person2["name"] as? String else {
            fatalError("Dictionary must contain 'name' key and value of type String.")
        }
        return name1 < name2
    }
    return sortedPeople.compactMap { $0["name"] as? String }
}
```

Differences from Senior 1 to Senior 2:

-   Mastery of software engineering principles, including clean code, SOLID
    principles, and design patterns.
-   The ability to effectively mentor and lead other developers, including
    conducting code reviews, providing feedback, and setting technical
    direction.
-   Strong communication skills and the ability to effectively collaborate with
    cross-functional teams.

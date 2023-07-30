# Task 3

Task: You have an array of dictionaries representing people's information, with
keys for "name", "age", and "city". Write a function that takes in this array
and returns a dictionary where the keys are the unique cities in the array, and
the values are arrays of people in that city, sorted by age from oldest to
youngest.

Solution:

```swift
func sortPeopleByCity(_ people: [[String: Any]]) -> [String: [[String: Any]]] {
    var sortedPeople = [String: [[String: Any]]]()
    for person in people {
        let city = person["city"] as! String
        if var peopleInCity = sortedPeople[city] {
            peopleInCity.append(person)
            sortedPeople[city] = peopleInCity.sorted(by: { (a, b) -> Bool in
                return (a["age"] as! Int) > (b["age"] as! Int)
            })
        } else {
            sortedPeople[city] = [person]
        }
    }
    return sortedPeople
}
```

Differences from the previous level (Middle 2) include:

-   Use of **`if var`** to check if a dictionary entry already exists, and
    modify it if it does
-   Use of **`sorted(by:)`** to sort the people in each city by age
-   Use of **`[[String: Any]]`** instead of **`Array<Any>`** to make the types
    more specific and avoid unnecessary typecasting later on.

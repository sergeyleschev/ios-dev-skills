# Task 2

Task: Create a function that fetches a JSON file from an external API and parses
it into a Swift struct, using URLSession and Codable.

Solution:

```swift
struct User: Codable {
    let name: String
    let username: String
    let email: String
}

func fetchUsers(completion: @escaping ([User]?) -> Void) {
    guard let url = URL(string: "https://jsonplaceholder.typicode.com/users") else {
        completion(nil)
        return
    }

    URLSession.shared.dataTask(with: url) { data, _, error in
        if let error = error {
            print("Error fetching users: \(error)")
            completion(nil)
            return
        }

        guard let data = data else {
            completion(nil)
            return
        }

        do {
            let users = try JSONDecoder().decode([User].self, from: data)
            completion(users)
        } catch {
            print("Error parsing users: \(error)")
            completion(nil)
        }
    }.resume()
}
```

Differences from Junior Level 2 solution:

-   The use of **`URLSession`** to fetch data asynchronously instead of
    synchronous **`Data(contentsOf:)`** method.
-   The use of **`Codable`** protocol to parse JSON into Swift struct instead of
    manually parsing the JSON data.

# Task 5

Task:

Create a function that fetches data from an API and parses it into a custom data
model. The API endpoint returns JSON data in the following format:

```json
{
    "name": "John Doe",
    "age": 25,
    "email": "johndoe@example.com"
}
```

Create a struct named **`Person`** that has properties for **`name`**,
**`age`**, and **`email`**. Then, create a function named **`fetchPerson`** that
takes a completion handler that returns a **`Person`** object. The function
should use the **`URLSession`** class to fetch data from the API endpoint, parse
the JSON response into a **`Person`** object, and return it in the completion
handler.

Solution:

```swift
struct Person {
    let name: String
    let age: Int
    let email: String
}

func fetchPerson(completion: @escaping (Person?) -> Void) {
    guard let url = URL(string: "https://example.com/api/person") else {
        completion(nil)
        return
    }

    let task = URLSession.shared.dataTask(with: url) { data, response, error in
        guard let data = data,
              let json = try? JSONSerialization.jsonObject(with: data, options: []),
              let dict = json as? [String: Any],
              let name = dict["name"] as? String,
              let age = dict["age"] as? Int,
              let email = dict["email"] as? String
        else {
            completion(nil)
            return
        }

        let person = Person(name: name, age: age, email: email)
        completion(person)
    }

    task.resume()
}
```

Differences from Junior 2:

In this task, the developer needs to understand how to make HTTP requests to an
API and parse the response into a custom data model. This requires a deeper
understanding of the **`URLSession`** class and JSON serialization than the
previous tasks. The developer also needs to understand how to use completion
handlers to return the parsed data asynchronously. Overall, this task requires a
higher level of proficiency with client-server communication than the previous
tasks.

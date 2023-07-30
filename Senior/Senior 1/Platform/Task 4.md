# Task 4

Task: Implement a network layer using the Combine framework to make a GET
request to an external API and parse the JSON response into a model object. The
endpoint URL and model structure will be provided.

Requirements:

-   Use Combine to make the network request and parse the response.
-   Use generics to make the network layer reusable for different endpoints.
-   Handle any errors that may occur during the network request or JSON parsing.
-   Use a completion handler to return the result to the caller.

Example usage:

```swift
// Define the model structure
struct User: Decodable {
    let id: Int
    let name: String
    let email: String
}

// Define the API endpoint URL
let endpoint = URL(string: "https://jsonplaceholder.typicode.com/users/1")!

// Make the network request
NetworkLayer.request(endpoint: endpoint) { result: Result<User, Error> in
    switch result {
    case .success(let user):
        print("User ID: \(user.id)")
        print("User Name: \(user.name)")
        print("User Email: \(user.email)")
    case .failure(let error):
        print("Error: \(error.localizedDescription)")
    }
}
```

Note: The goal of this task is to demonstrate the ability to use Combine to make
network requests and parse JSON responses into model objects. This is a skill
that is highly valued in senior iOS developers, as it allows them to integrate
with APIs more easily and efficiently.

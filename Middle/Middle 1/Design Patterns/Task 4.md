# Task 4

## **Task**

You're building an app that has multiple API endpoints, each requiring a unique
authentication token. Rather than having the authentication logic for each
endpoint scattered throughout the app, you want to create a simple API client
facade that abstracts away the authentication details and makes it easy to call
the various endpoints. Your task is to create the **`ApiClientFacade`** class,
which should have the following requirements:

1. The **`ApiClientFacade`** should be responsible for authentication and should
   store the authentication tokens for each endpoint.
2. The **`ApiClientFacade`** should provide methods for each API endpoint that
   abstract away the authentication details and return the parsed response.
3. The **`ApiClientFacade`** should use the **`URLSession`** API for making
   network requests.

You can use the following mock API endpoints for testing:

-   **`https://example.com/api/users`**
-   **`https://example.com/api/posts`**
-   **`https://example.com/api/comments`**

The authentication tokens can be hard-coded for the sake of this exercise.

## **Solution**

Here's an example implementation of the **`ApiClientFacade`** class:

```swift
class ApiClientFacade {
    private let usersToken = "users_token"
    private let postsToken = "posts_token"
    private let commentsToken = "comments_token"

    private func getAuthToken(for endpoint: String) -> String {
        switch endpoint {
        case "users":
            return usersToken
        case "posts":
            return postsToken
        case "comments":
            return commentsToken
        default:
            fatalError("Invalid endpoint")
        }
    }

    private func makeRequest(for endpoint: String, completion: @escaping (Result<Data, Error>) -> Void) {
        guard let url = URL(string: "https://example.com/api/\(endpoint)") else {
            completion(.failure(NSError(domain: "Invalid URL", code: 0, userInfo: nil)))
            return
        }

        var request = URLRequest(url: url)
        request.addValue(getAuthToken(for: endpoint), forHTTPHeaderField: "Authorization")

        URLSession.shared.dataTask(with: request) { data, response, error in
            if let error = error {
                completion(.failure(error))
                return
            }

            guard let data = data else {
                completion(.failure(NSError(domain: "No data", code: 0, userInfo: nil)))
                return
            }

            completion(.success(data))
        }.resume()
    }

    func getUsers(completion: @escaping (Result<[User], Error>) -> Void) {
        makeRequest(for: "users") { result in
            switch result {
            case .success(let data):
                // Parse JSON data and return array of User objects
                completion(.success(users))
            case .failure(let error):
                completion(.failure(error))
            }
        }
    }

    func getPosts(completion: @escaping (Result<[Post], Error>) -> Void) {
        makeRequest(for: "posts") { result in
            switch result {
            case .success(let data):
                // Parse JSON data and return array of Post objects
                completion(.success(posts))
            case .failure(let error):
                completion(.failure(error))
            }
        }
    }

    func getComments(completion: @escaping (Result<[Comment], Error>) -> Void) {
        makeRequest(for: "comments") { result in
            switch result {
            case .success(let data):
                // Parse JSON data and return array of Comment objects
                completion(.success(comments))
            case .failure(let error):
                completion(.failure(error))
            }
        }
    }
}
```

This implementation follows the Facade pattern by abstracting away the
authentication details and making it easy to call each API endpoint with a
simple method call.

# Task 4

Task:

You are working on a project that heavily relies on network requests. You notice
that the codebase has a lot of callbacks and nested closures that make it
difficult to read and maintain. Your team lead suggests that you explore using
Reactive Programming and specifically, the Combine framework to simplify the
codebase. Your task is to refactor an existing network request method to use
Combine.

Code to refactor:

```swift
func fetchUserPosts(userId: Int, completion: @escaping ([Post]?, Error?) -> Void) {
    let endpoint = "https://jsonplaceholder.typicode.com/posts?userId=\(userId)"
    guard let url = URL(string: endpoint) else { return }
    URLSession.shared.dataTask(with: url) { (data, response, error) in
        if let error = error {
            completion(nil, error)
            return
        }
        guard let data = data else {
            completion(nil, NetworkError.noData)
            return
        }
        do {
            let posts = try JSONDecoder().decode([Post].self, from: data)
            completion(posts, nil)
        } catch {
            completion(nil, NetworkError.decodingError)
        }
    }.resume()
}
```

Refactored solution using Combine:

```swift
import Combine

func fetchUserPosts(userId: Int) -> AnyPublisher<[Post], Error> {
    let endpoint = "https://jsonplaceholder.typicode.com/posts?userId=\(userId)"
    guard let url = URL(string: endpoint) else {
        return Fail(error: NetworkError.invalidEndpoint).eraseToAnyPublisher()
    }
    return URLSession.shared.dataTaskPublisher(for: url)
        .map { $0.data }
        .decode(type: [Post].self, decoder: JSONDecoder())
        .eraseToAnyPublisher()
}
```

Differences from Junior 3 level:

-   This task involves refactoring existing code to use a new framework, rather
    than just implementing new functionality.
-   The solution involves using Combine to simplify asynchronous code,
    demonstrating knowledge of a popular functional reactive programming
    paradigm.
-   The solution uses operators like **`map`** and **`decode`** that are
    specific to Combine, demonstrating knowledge of how to use Combine
    effectively.

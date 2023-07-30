# Task 1

Task: Given a Swift class with a method that takes a closure as an argument and
returns a value asynchronously using GCD, rewrite the method to use the new
async/await syntax introduced in Swift 5.5.

Example Swift class with method using GCD:

```swift
class MyViewController: UIViewController {
    func fetchData(completion: @escaping (Result<String, Error>) -> Void) {
        DispatchQueue.global().async {
            // Simulate fetching data from a remote server
            sleep(3)
            let result: Result<String, Error> = .success("Data loaded successfully")
            DispatchQueue.main.async {
                completion(result)
            }
        }
    }
}
```

Solution using async/await syntax:

```swift
class MyViewController: UIViewController {
    func fetchData() async throws -> String {
        try await withUnsafeThrowingContinuation { continuation in
            DispatchQueue.global().async {
                // Simulate fetching data from a remote server
                sleep(3)
                let result: Result<String, Error> = .success("Data loaded successfully")
                continuation.resume(returning: result)
            }
        }
    }
}
```

Differences that indicate the development of the developer to the level of
Senior 2 from the level of Senior 1:

-   Understanding of async/await syntax and how to use it to simplify
    asynchronous code
-   Ability to handle errors using async/await and throwing functions
-   Familiarity with Swift 5.5 features and ability to use them effectively in
    code.

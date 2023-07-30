# Task 3

Task: Implement a network layer using the Singleton pattern to handle all
network requests in your iOS application. The network layer should support GET
and POST requests, handle errors appropriately, and use URLSession for network
calls.

Solution:

```swift
class NetworkManager {

    static let shared = NetworkManager()
    private let session = URLSession.shared

    func performGetRequest(url: URL, completionHandler: @escaping (Result<Data, Error>) -> Void) {
        let task = session.dataTask(with: url) { data, response, error in
            if let error = error {
                completionHandler(.failure(error))
                return
            }

            guard let httpResponse = response as? HTTPURLResponse else {
                completionHandler(.failure(NSError(domain: "NetworkManager", code: 0, userInfo: nil)))
                return
            }

            guard 200 ..< 300 ~= httpResponse.statusCode else {
                completionHandler(.failure(NSError(domain: "NetworkManager", code: httpResponse.statusCode, userInfo: nil)))
                return
            }

            guard let data = data else {
                completionHandler(.failure(NSError(domain: "NetworkManager", code: 0, userInfo: nil)))
                return
            }

            completionHandler(.success(data))
        }

        task.resume()
    }

    func performPostRequest(url: URL, body: Data?, completionHandler: @escaping (Result<Data, Error>) -> Void) {
        var request = URLRequest(url: url)
        request.httpMethod = "POST"
        request.httpBody = body

        let task = session.dataTask(with: request) { data, response, error in
            if let error = error {
                completionHandler(.failure(error))
                return
            }

            guard let httpResponse = response as? HTTPURLResponse else {
                completionHandler(.failure(NSError(domain: "NetworkManager", code: 0, userInfo: nil)))
                return
            }

            guard 200 ..< 300 ~= httpResponse.statusCode else {
                completionHandler(.failure(NSError(domain: "NetworkManager", code: httpResponse.statusCode, userInfo: nil)))
                return
            }

            guard let data = data else {
                completionHandler(.failure(NSError(domain: "NetworkManager", code: 0, userInfo: nil)))
                return
            }

            completionHandler(.success(data))
        }

        task.resume()
    }
}
```

Differences from Senior (1 of 2):

-   This task requires knowledge of the Singleton pattern, which is a more
    advanced design pattern than Dependency Injection and Service Locator.
-   The task requires the implementation of a complete network layer that
    supports GET and POST requests, error handling, and URLSession. This
    requires more knowledge of iOS networking than the previous task.
-   The solution uses Result and guard statements for better error handling and
    more concise code.
-   The task and solution overall require more advanced knowledge and expertise
    in iOS development.

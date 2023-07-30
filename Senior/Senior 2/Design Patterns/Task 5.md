# Task 5

Task: You have been assigned to refactor an existing iOS app that uses several
network APIs to fetch data. Currently, the app uses a singleton network manager
that handles all API requests. However, you have noticed that this approach
makes it difficult to test and also creates a tight coupling between the network
manager and other parts of the app.

Your task is to refactor the app to use a dependency injection approach for
network requests. Implement a class that handles network requests using
URLSession and allow it to be injected into the appropriate parts of the app.

Solution: First, create a NetworkService protocol that defines the methods that
will be used for API requests:

```swift
protocol NetworkService {
    func fetchData(from url: URL, completion: @escaping (Result<Data, Error>) -> Void)
}
```

Next, create a NetworkManager class that implements the NetworkService protocol
using URLSession:

```swift
class NetworkManager: NetworkService {
    func fetchData(from url: URL, completion: @escaping (Result<Data, Error>) -> Void) {
        URLSession.shared.dataTask(with: url) { data, response, error in
            if let error = error {
                completion(.failure(error))
                return
            }
            guard let httpResponse = response as? HTTPURLResponse, (200..<300).contains(httpResponse.statusCode) else {
                completion(.failure(NetworkError.invalidResponse))
                return
            }
            guard let data = data else {
                completion(.failure(NetworkError.noData))
                return
            }
            completion(.success(data))
        }.resume()
    }
}
```

Finally, inject the NetworkService into the appropriate parts of the app, such
as view controllers or other services:

```swift
class MyViewController: UIViewController {
    let networkService: NetworkService

    init(networkService: NetworkService) {
        self.networkService = networkService
        super.init(nibName: nil, bundle: nil)
    }

    required init?(coder: NSCoder) {
        fatalError("init(coder:) has not been implemented")
    }

    func fetchData() {
        guard let url = URL(string: "https://example.com/api/data") else { return }
        networkService.fetchData(from: url) { result in
            switch result {
            case .success(let data):
                // handle data
            case .failure(let error):
                // handle error
            }
        }
    }
}
```

Differences indicating development from Senior 1 to Senior 2:

-   In this task, the developer is asked to refactor an existing app, which
    requires a deeper understanding of the codebase and the ability to identify
    areas for improvement.
-   The task requires the implementation of a protocol and dependency injection,
    which demonstrates a more advanced understanding of design patterns.
-   The code is expected to be well-structured, modular, and testable, which
    shows a higher level of concern for code quality and maintainability.

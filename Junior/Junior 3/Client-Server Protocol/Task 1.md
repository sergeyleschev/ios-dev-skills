# Task 1

Task: Write a function that makes a GET request to a specified API endpoint and
decodes the response JSON into a model object.

Technical Requirements:

-   Use the URLSession and Codable APIs.
-   Handle errors and edge cases gracefully.

Solution:

```swift
func fetchModel<T: Decodable>(from endpoint: String, completion: @escaping (Result<T, Error>) -> Void) {
    guard let url = URL(string: endpoint) else {
        completion(.failure(NetworkError.invalidURL))
        return
    }

    URLSession.shared.dataTask(with: url) { data, response, error in
        if let error = error {
            completion(.failure(error))
            return
        }

        guard let data = data else {
            completion(.failure(NetworkError.invalidData))
            return
        }

        do {
            let decoder = JSONDecoder()
            let model = try decoder.decode(T.self, from: data)
            completion(.success(model))
        } catch let error {
            completion(.failure(error))
        }
    }.resume()
}
```

Differences from Junior 2 level:

-   The function signature now includes a generic type parameter **`T`**,
    allowing the caller to specify the model object they expect to receive.
-   The function now uses the **`JSONDecoder`** API to decode the JSON response
    into the specified model object.
-   The function now handles more error cases, including invalid URLs and
    invalid data.

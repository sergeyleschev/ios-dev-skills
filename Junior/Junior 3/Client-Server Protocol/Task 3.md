# Task 3

Task: Implement a function that sends a POST request to a server with JSON data
in the request body, and parses the response JSON into a Swift struct. The
function should have the following signature:

```swift
func sendJSONRequest<T: Decodable>(url: URL, data: Encodable, completion: @escaping (Result<T, Error>) -> Void)
```

The function should use the URLSession API to perform the request and handle
errors appropriately. The request body should be encoded using JSONEncoder and
the response should be decoded into the provided **`T`** type using JSONDecoder.
If the request is successful, the completion block should be called with a
**`.success`** result containing the parsed struct. If there is an error, the
completion block should be called with a **`.failure`** result containing the
error.

Solution:

```swift
func sendJSONRequest<T: Decodable>(url: URL, data: Encodable, completion: @escaping (Result<T, Error>) -> Void) {
    var request = URLRequest(url: url)
    request.httpMethod = "POST"
    request.setValue("application/json", forHTTPHeaderField: "Content-Type")
    do {
        request.httpBody = try JSONEncoder().encode(data)
    } catch {
        completion(.failure(error))
        return
    }
    let task = URLSession.shared.dataTask(with: request) { data, response, error in
        if let error = error {
            completion(.failure(error))
            return
        }
        guard let httpResponse = response as? HTTPURLResponse,
              (200...299).contains(httpResponse.statusCode) else {
            completion(.failure(NSError(domain: NSURLErrorDomain, code: NSURLErrorBadServerResponse, userInfo: nil)))
            return
        }
        guard let data = data else {
            completion(.failure(NSError(domain: NSURLErrorDomain, code: NSURLErrorDataLengthExceedsMaximum, userInfo: nil)))
            return
        }
        do {
            let parsedObject = try JSONDecoder().decode(T.self, from: data)
            completion(.success(parsedObject))
        } catch {
            completion(.failure(error))
        }
    }
    task.resume()
}
```

The key differences between a Junior 2 and a Junior 3 developer in this task
would be the ability to:

1. Use generics (**`<T: Decodable>`**) to make the function reusable for any
   struct that conforms to the Decodable protocol, instead of having to write a
   separate function for each specific struct.
2. Use the **`Result`** type instead of throwing errors, which makes the
   function more flexible and easier to use in asynchronous contexts.
3. Handle errors more gracefully, including checking for a valid HTTP response
   code and providing appropriate error messages in the completion block.

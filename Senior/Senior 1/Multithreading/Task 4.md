# Task 4

Task: Write a method to asynchronously fetch data from a remote API using
URLSession, and return the result using a completion handler. The method should
also handle errors and retries if the request fails.

Solution:

```swift
func fetchData(completion: @escaping (Result<Data, Error>) -> Void) {
    let url = URL(string: "https://example.com/data")!
    var request = URLRequest(url: url)
    request.httpMethod = "GET"

    let task = URLSession.shared.dataTask(with: request) { data, response, error in
        if let error = error {
            // Handle the error and retry the request
            // up to 3 times before giving up
            var retries = 0
            repeat {
                retries += 1
                sleep(2) // Wait for 2 seconds before retrying
                URLSession.shared.dataTask(with: request) { data, response, error in
                    if let error = error {
                        if retries >= 3 {
                            completion(.failure(error))
                        }
                    } else if let data = data {
                        completion(.success(data))
                    }
                }.resume()
            } while retries < 3
        } else if let data = data {
            completion(.success(data))
        }
    }
    task.resume()
}
```

Differences from the previous level:

This task requires the developer to understand more advanced concepts in
multithreading, such as handling errors and retries when fetching data
asynchronously. Additionally, the task requires the use of the **`sleep()`**
method to wait for a period of time before retrying the request, which can lead
to blocking issues if not used correctly. The solution also uses a completion
handler to return the result of the asynchronous task, which is a common pattern
in senior-level iOS development.

# Task 4

Task: Implement a Facade design pattern to simplify a complex subsystem of
networking classes. Your goal is to create a Facade class that hides the
complexity of the subsystem and provides a simple interface for the client code
to use.

Solution:

```swift
import Foundation

class NetworkFacade {
    let session: URLSession

    init(session: URLSession = URLSession.shared) {
        self.session = session
    }

    func fetchData(from url: URL, completion: @escaping (Result<Data, Error>) -> Void) {
        let task = session.dataTask(with: url) { (data, response, error) in
            if let error = error {
                completion(.failure(error))
                return
            }
            guard let httpResponse = response as? HTTPURLResponse,
                  (200...299).contains(httpResponse.statusCode) else {
                completion(.failure(NSError(domain: "Invalid response", code: 0, userInfo: nil)))
                return
            }
            guard let data = data else {
                completion(.failure(NSError(domain: "No data", code: 0, userInfo: nil)))
                return
            }
            completion(.success(data))
        }
        task.resume()
    }
}
```

In this example, we've created a **`NetworkFacade`** class that hides the
complexity of the **`URLSession`** networking subsystem. It provides a simple
interface for fetching data from a URL, and returns the data to the client code
in a closure. The client code doesn't need to worry about the underlying
networking details, such as handling errors or parsing responses, because that
logic is encapsulated in the **`NetworkFacade`**.

To point out the differences between the middle 1 and middle 2 level, the middle
2 developer is expected to be able to apply design patterns to more complex
scenarios, and to be able to write more robust and scalable code. In this
example, the middle 2 developer has applied the Facade pattern to a complex
subsystem, which shows an understanding of the pattern and the ability to apply
it to real-world scenarios. Additionally, the use of closures and **`Result`**
types in the completion handler make the code more robust and scalable, which is
an important skill for a mid-level developer.

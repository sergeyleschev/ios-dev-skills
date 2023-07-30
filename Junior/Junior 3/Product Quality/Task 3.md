# Task 3

Task: Write a function that tests whether a given API endpoint returns a valid
JSON response. The function should take in the endpoint URL as a string and
return a boolean value indicating whether the response is valid or not.

Solution:

```swift
func testAPIEndpoint(urlString: String) -> Bool {
    guard let url = URL(string: urlString) else {
        return false
    }

    let session = URLSession.shared

    let semaphore = DispatchSemaphore(value: 0)

    var isValid = false

    let task = session.dataTask(with: url) { (data, response, error) in
        if let error = error {
            print("Error: \(error.localizedDescription)")
        } else if let data = data {
            do {
                let json = try JSONSerialization.jsonObject(with: data, options: [])
                if json is [String: Any] {
                    isValid = true
                }
            } catch {
                print("Error: \(error.localizedDescription)")
            }
        }
        semaphore.signal()
    }

    task.resume()

    _ = semaphore.wait(timeout: .now() + 5)

    return isValid
}
```

To indicate the development of the developer to the level of junior 3, the
interviewer should look for the following differences:

-   Code quality: A junior 3 developer should have a better understanding of
    good coding practices and should be able to write more efficient and
    maintainable code. This can be demonstrated by things like better code
    organization, more efficient algorithms, and more elegant syntax.
-   Error handling: A junior 3 developer should be able to handle errors in a
    more robust and graceful way. This can be demonstrated by things like using
    try-catch blocks for error handling, providing meaningful error messages,
    and handling errors at different levels of the application.
-   Testing: A junior 3 developer should have a better understanding of testing
    and should be able to write more comprehensive test cases. This can be
    demonstrated by things like writing unit tests and integration tests, using
    mocking and stubbing to isolate dependencies, and writing testable code.

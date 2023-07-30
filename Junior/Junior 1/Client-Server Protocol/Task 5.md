# Task 5

## **Task:**

Write a function that sends a GET request to an API endpoint and returns an
array of dictionaries parsed from the JSON response. The API endpoint is
**`https://jsonplaceholder.typicode.com/users`** and it returns an array of user
objects in JSON format. Your function should accept a completion handler that
returns the parsed array of dictionaries or an error.

The function signature should be:

```swift
func getUsers(completion: @escaping ([[String: Any]]?, Error?) -> Void)

```

## **Solution:**

```swift
func getUsers(completion: @escaping ([[String: Any]]?, Error?) -> Void) {
    guard let url = URL(string: "https://jsonplaceholder.typicode.com/users") else {
        completion(nil, NSError(domain: "Invalid URL", code: 0, userInfo: nil))
        return
    }

    URLSession.shared.dataTask(with: url) { (data, response, error) in
        if let error = error {
            completion(nil, error)
            return
        }

        guard let data = data else {
            completion(nil, NSError(domain: "No data received", code: 0, userInfo: nil))
            return
        }

        do {
            if let json = try JSONSerialization.jsonObject(with: data, options: []) as? [[String: Any]] {
                completion(json, nil)
            } else {
                completion(nil, NSError(domain: "Invalid JSON format", code: 0, userInfo: nil))
            }
        } catch let error {
            completion(nil, error)
        }
    }.resume()
}

```

This function first creates a URL object from the API endpoint. It then uses
URLSession to send a GET request to the endpoint. If an error occurs during the
request or if no data is received, an appropriate error is returned to the
completion handler. If the request is successful and data is received, the data
is parsed into an array of dictionaries using JSONSerialization. The resulting
array of dictionaries is returned to the completion handler. If the JSON is
invalid, an error is returned instead.

# Task 1

## **Task:**

Write a function that sends a POST request to an API endpoint and returns a
dictionary parsed from the JSON response. The API endpoint is
**`https://jsonplaceholder.typicode.com/posts`** and it expects a JSON payload
in the request body. The payload should include the **`userId`**, **`id`**,
**`title`**, and **`body`** fields.

The function signature should be:

```swift
func createPost(userId: Int, id: Int, title: String, body: String, completion: @escaping ([String: Any]?, Error?) -> Void)
```

## **Solution:**

```swift
func createPost(userId: Int, id: Int, title: String, body: String, completion: @escaping ([String: Any]?, Error?) -> Void) {
    guard let url = URL(string: "https://jsonplaceholder.typicode.com/posts") else {
        completion(nil, NSError(domain: "Invalid URL", code: 0, userInfo: nil))
        return
    }

    let json: [String: Any] = ["userId": userId, "id": id, "title": title, "body": body]
    let jsonData = try? JSONSerialization.data(withJSONObject: json)

    var request = URLRequest(url: url)
    request.httpMethod = "POST"
    request.httpBody = jsonData
    request.setValue("application/json", forHTTPHeaderField: "Content-Type")

    URLSession.shared.dataTask(with: request) { (data, response, error) in
        if let error = error {
            completion(nil, error)
            return
        }

        guard let data = data else {
            completion(nil, NSError(domain: "No data received", code: 0, userInfo: nil))
            return
        }

        do {
            if let json = try JSONSerialization.jsonObject(with: data, options: []) as? [String: Any] {
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

### **Differences from Junior 1 level:**

-   This task involves sending a POST request instead of a GET request. This
    requires setting the HTTP method to "POST" and including a request body with
    the payload.
-   The payload for this task includes multiple fields instead of just one. This
    requires creating a dictionary with multiple key-value pairs and encoding it
    as JSON data.
-   The completion handler for this task returns a single dictionary instead of
    an array of dictionaries. This reflects the fact that the API endpoint for
    this task returns a single object instead of an array.

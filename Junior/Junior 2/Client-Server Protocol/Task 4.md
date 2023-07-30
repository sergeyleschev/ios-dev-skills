# Task 4

Task: Implement a function that makes an HTTP GET request to a given URL and
parses the response JSON into an array of custom model objects. The function
should handle errors and return either the array of model objects or an error.

Solution:

```swift
func fetchModels(from url: URL, completion: @escaping ([Model]?, Error?) -> Void) {
    URLSession.shared.dataTask(with: url) { data, response, error in
        guard error == nil else {
            completion(nil, error)
            return
        }
        guard let data = data else {
            completion(nil, NSError(domain: "com.example.app", code: -1, userInfo: [NSLocalizedDescriptionKey: "No data returned"]))
            return
        }
        do {
            let models = try JSONDecoder().decode([Model].self, from: data)
            completion(models, nil)
        } catch {
            completion(nil, error)
        }
    }.resume()
}

```

Differences from the Junior 1 level:

-   The function now takes a completion handler, which allows for asynchronous
    processing and returning of the result.
-   Error handling has been improved to handle both networking errors and
    decoding errors, and return them through the completion handler.
-   The function now uses a **`URLSession`** to make the network request, which
    is the recommended way to perform networking in iOS development.
-   The response JSON is decoded into an array of custom model objects, rather
    than just a generic **`Any`** object.

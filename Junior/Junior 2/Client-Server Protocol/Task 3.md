# Task 3

Task: Create a function that performs a GET request to a JSON API endpoint and
returns an array of objects.

Solution:

```swift
func getObjectsFromAPI(completion: @escaping ([Object]?, Error?) -> Void) {
    let url = URL(string: "https://example.com/api/objects")!
    URLSession.shared.dataTask(with: url) { data, response, error in
        if let error = error {
            completion(nil, error)
            return
        }
        guard let data = data else {
            completion(nil, NSError(domain: "com.example.error", code: 0, userInfo: [NSLocalizedDescriptionKey: "Data was not received."]))
            return
        }
        do {
            let objects = try JSONDecoder().decode([Object].self, from: data)
            completion(objects, nil)
        } catch {
            completion(nil, error)
        }
    }.resume()
}

```

In this solution, we create a function that takes a completion handler with an
array of **`Object`** objects and an **`Error`** object as parameters. The
function performs a GET request to the specified API endpoint using
**`URLSession.shared.dataTask`**, and then attempts to decode the received JSON
data into an array of **`Object`** objects using **`JSONDecoder`**. If
successful, the array is passed to the completion handler. If an error occurs at
any point, it is also passed to the completion handler. This task demonstrates
the developer's proficiency in handling asynchronous network requests and
parsing JSON data.

# Task 5

Task: Given a list of URLs, fetch the contents of each URL in a separate
background thread and display them in the UI when all the downloads have
completed.

Solution:

```swift
func fetchURLContents(_ urls: [URL], completion: @escaping ([String]) -> Void) {
    var contents: [String] = []
    let group = DispatchGroup()
    let queue = DispatchQueue.global(qos: .userInitiated)
    for url in urls {
        group.enter()
        queue.async {
            if let data = try? Data(contentsOf: url), let content = String(data: data, encoding: .utf8) {
                contents.append(content)
            }
            group.leave()
        }
    }
    group.notify(queue: DispatchQueue.main) {
        completion(contents)
    }
}
```

Here, we use a dispatch group to keep track of when all the downloads have
completed, and notify the main thread when they have. We also use a global
background queue to download the contents of each URL, rather than relying on
**`asyncAfter`** to schedule them at a later time. Additionally, we use a
completion handler to pass the fetched contents back to the caller.

Some of the differences that distinguish this task from the previous Junior
level tasks are:

1. The use of dispatch groups and a global background queue to handle
   concurrency, rather than relying solely on **`asyncAfter`**.
2. The use of a completion handler to pass the fetched contents back to the
   caller, rather than updating the UI directly from the background thread.
3. The use of more advanced techniques such as error handling (**`try?`**) and
   **`String`** encoding (**`utf8`**).

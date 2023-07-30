# Task 5

Task: Write a function that retrieves data from a web API asynchronously, and
displays it on the screen in a table view. Use Grand Central Dispatch to perform
the API call in the background.

Solution:

```swift
func fetchDataFromAPI() {
    DispatchQueue.global(qos: .userInitiated).async {
        guard let url = URL(string: "https://jsonplaceholder.typicode.com/posts") else {
            print("Invalid URL")
            return
        }

        URLSession.shared.dataTask(with: url) { data, response, error in
            if let error = error {
                print("Error retrieving data: \(error.localizedDescription)")
                return
            }

            guard let httpResponse = response as? HTTPURLResponse,
                  (200...299).contains(httpResponse.statusCode) else {
                print("Invalid response")
                return
            }

            guard let data = data else {
                print("No data received")
                return
            }

            do {
                let posts = try JSONDecoder().decode([Post].self, from: data)

                DispatchQueue.main.async {
                    // assuming you have a table view in your view controller
                    self.tableView.reloadData()
                }
            } catch let error {
                print("Error decoding data: \(error.localizedDescription)")
                return
            }
        }.resume()
    }
}
```

This task builds upon the previous task by introducing the use of APIs and
networking. The developer is expected to be able to make asynchronous network
calls, handle errors, and parse JSON data. The use of Grand Central Dispatch is
also emphasized, to ensure that the network call is performed on a background
thread to prevent blocking the main thread.

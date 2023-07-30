# Task 2

Task: Write a function that fetches a large amount of data from a server and
displays it in a table view. Ensure that the data is loaded efficiently and
without causing any memory leaks.

Solution:

```swift
func fetchData() {
    guard let url = URL(string: "https://example.com/largeData") else {
        print("Invalid URL")
        return
    }

    let task = URLSession.shared.dataTask(with: url) { [weak self] data, response, error in
        guard let data = data, error == nil else {
            print("Error fetching data: \(error?.localizedDescription ?? "Unknown error")")
            return
        }

        // Parse data and create table view model
        let tableViewModel = createTableViewModel(from: data)

        // Ensure we're on the main thread before updating UI
        DispatchQueue.main.async { [weak self] in
            // Display table view with the new data
            self?.tableViewModel = tableViewModel
            self?.tableView.reloadData()
        }
    }

    task.resume()
}
```

The key difference between this task and the previous ones is that it requires
the developer to handle efficiently loading a large amount of data, while also
ensuring that there are no memory leaks caused by retaining references to the
data or other objects. In the solution, we use a weak reference to **`self`** to
avoid creating a strong reference cycle and use **`DispatchQueue.main.async`**
to ensure that the UI updates are done on the main thread.

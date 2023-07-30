# Task 4

Task: You're working on an app that needs to fetch data from a web API and
display it in a table view. The API is slow and sometimes takes several seconds
to respond. Currently, the app makes the API call synchronously on the main
thread, which causes the app to freeze while waiting for a response. Improve the
app's performance by making the API call asynchronously and displaying the
results in the table view once they are available. However, you also need to
ensure that the user doesn't see any inconsistent data or glitches while the
table view is being updated.

Solution:

```swift
// Make the API call asynchronously on a background queue
DispatchQueue.global(qos: .userInitiated).async {
    // Make the API request
    let url = URL(string: "https://example.com/api/data")!
    let data = try! Data(contentsOf: url)
    let items = try! JSONDecoder().decode([Item].self, from: data)

    // Update the table view on the main thread
    DispatchQueue.main.async {
        // Only update the table view if it's still visible
        if let indexPaths = self.tableView.indexPathsForVisibleRows {
            self.items = items
            self.tableView.reloadRows(at: indexPaths, with: .automatic)
        }
    }
}
```

Explanation:

In the above solution, we're making the API call asynchronously on a background
queue using **`DispatchQueue.global(qos: .userInitiated).async`**. This ensures
that the main thread isn't blocked while waiting for the API response. Once the
API response is available, we're updating the table view on the main thread
using **`DispatchQueue.main.async`**. We're also checking if the table view is
still visible by checking if **`indexPathsForVisibleRows`** is not nil. If the
table view is not visible, we don't update it to avoid any inconsistent data or
glitches.

The key difference between this task and the Junior (3 of 3) level task is that
in this task, we're not using **`asyncAfter`** and thread synchronization to
solve the problem. Instead, we're using Grand Central Dispatch (GCD) to make the
API call asynchronously on a background queue and update the table view on the
main thread. This requires a deeper understanding of GCD and thread safety,
which is a skill typically expected of Middle level iOS Developers.

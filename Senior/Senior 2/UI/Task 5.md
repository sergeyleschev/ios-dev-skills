# Task 5

Task:

Create a reusable view controller that displays a list of items in a
UITableView. The view controller should support both single and multi-select
modes, and should display a checkmark next to selected items.

Solution:

1. Create a new file called **`ListViewController.swift`** and import UIKit.

```swift
import UIKit
```

2. Create a new class called **`ListViewController`** that subclasses
   UITableViewController.

```swift
class ListViewController: UITableViewController {

}
```

3. Add properties to support single and multi-select modes, and to hold the list
   of items and selected items.

```swift
var singleSelectMode: Bool = false
var items: [String] = []
var selectedItems: Set<String> = []
```

4. Override the **`numberOfSections`** method to return 1.

```swift
override func numberOfSections(in tableView: UITableView) -> Int {
    return 1
}
```

5. Override the **`tableView(_:numberOfRowsInSection:)`** method to return the
   number of items in the list.

```swift
override func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
    return items.count
}
```

6. Override the **`tableView(_:cellForRowAt:)`** method to configure the cell
   and display a checkmark if the item is selected.

```swift
override func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
    let cell = tableView.dequeueReusableCell(withIdentifier: "cell", for: indexPath)
    cell.textLabel?.text = items[indexPath.row]

    if selectedItems.contains(items[indexPath.row]) {
        cell.accessoryType = .checkmark
    } else {
        cell.accessoryType = .none
    }

    return cell
}
```

7. Override the **`tableView(_:didSelectRowAt:)`** method to toggle the
   selection of the item and update the UI.

```swift
override func tableView(_ tableView: UITableView, didSelectRowAt indexPath: IndexPath) {
    if singleSelectMode {
        selectedItems.removeAll()
    }

    let selectedItem = items[indexPath.row]
    if selectedItems.contains(selectedItem) {
        selectedItems.remove(selectedItem)
    } else {
        selectedItems.insert(selectedItem)
    }

    tableView.reloadRows(at: [indexPath], with: .none)
}
```

8. Build and run the app, and create a **`ListViewController`** instance with
   some items and selected items. Set the **`singleSelectMode`** property to
   **`true`** or **`false`** depending on the desired mode.

Differences from Senior 1 level:

-   The developer is able to create a reusable view controller that can display
    a list of items in a UITableView.
-   The developer knows how to support both single and multi-select modes, and
    how to display a checkmark next to selected items.
-   The developer understands the concept of delegation and can pass data back
    to the presenting view controller using a delegate.

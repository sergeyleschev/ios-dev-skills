# Task 1

Task:

Create a simple app that displays a list of items. Each item should have a title
and a subtitle. When an item is tapped, a detail view should appear with the
item's title and subtitle displayed. The detail view should also have a "Delete"
button that allows the user to delete the item. When an item is deleted, the
list view should update to remove the deleted item.

Technical Requirements:

-   Use UITableView to display the list of items.
-   Use a custom UITableViewCell subclass to display the title and subtitle.
-   Use a delegate pattern to communicate between the list view and the detail
    view.

Solution:

1. First, create a protocol called **`ItemSelectionDelegate`** with the
   following method:

```swift
protocol ItemSelectionDelegate: AnyObject {
    func didSelectItem(_ item: Item)
}
```

2. Next, create a **`ListViewController`** that displays a list of **`Item`**
   objects in a UITableView. Implement the **`UITableViewDataSource`** and
   **`UITableViewDelegate`** methods to display the title and subtitle of each
   item using a custom **`UITableViewCell`** subclass.

```swift
class ListViewController: UIViewController, UITableViewDataSource, UITableViewDelegate {

    var items: [Item] = []
    weak var delegate: ItemSelectionDelegate?

    // Implement UITableViewDataSource and UITableViewDelegate methods here

    func tableView(_ tableView: UITableView, didSelectRowAt indexPath: IndexPath) {
        let selectedItem = items[indexPath.row]
        delegate?.didSelectItem(selectedItem)
    }
}
```

3. Create a **`DetailViewController`** that displays the title and subtitle of
   an **`Item`**. Implement the **`ItemSelectionDelegate`** protocol to receive
   the selected item from the **`ListViewController`**. Add a "Delete" button
   that calls a method to delete the selected item.

```swift
class DetailViewController: UIViewController, ItemSelectionDelegate {

    var selectedItem: Item?

    // Add UI elements to display the selected item's title and subtitle here

    func didSelectItem(_ item: Item) {
        selectedItem = item
        // Update UI elements to display the selected item's title and subtitle
    }

    func deleteButtonTapped() {
        guard let selectedItem = selectedItem else { return }
        // Delete the selected item from the data source
        // Update the UI to remove the deleted item
    }
}
```

4. In the **`ListViewController`**, implement the **`ItemSelectionDelegate`**
   protocol to present the **`DetailViewController`** when an item is tapped.

```swift
class ListViewController: UIViewController, ItemSelectionDelegate {

    // Add code to display the list of items here

    func didSelectItem(_ item: Item) {
        let detailViewController = DetailViewController()
        detailViewController.delegate = self
        navigationController?.pushViewController(detailViewController, animated: true)
    }
}
```

Differences from Junior 1 Level:

The solution for this task is a step above the previous Junior level task as it
involves communicating data between two view controllers using a delegate
pattern, rather than just a single view controller. The
**`ItemSelectionDelegate`** protocol allows the **`ListViewController`** to
communicate with the **`DetailViewController`** and pass the selected **`Item`**
object. Additionally, the **`DetailViewController`** has a "Delete" button that
allows the user to delete the selected item, which requires updating the data
source and the UI of the **`ListViewController`**. This task requires a deeper
understanding of delegation and view controller communication than the previous
Junior level task.

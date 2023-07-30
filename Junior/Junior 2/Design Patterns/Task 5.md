# Task 5

Task: Implement a simple app that shows a list of items in a table view. The app
should have a data model, a view controller that displays the data, and a
separate class that manages the data.

Solution:

```swift
// Data Model
struct Item {
    let title: String
    let subtitle: String
}

// Data Manager
class ItemManager {
    var items: [Item] = [
        Item(title: "Item 1", subtitle: "Subtitle 1"),
        Item(title: "Item 2", subtitle: "Subtitle 2"),
        Item(title: "Item 3", subtitle: "Subtitle 3")
    ]
}

// View Controller
class ItemListViewController: UIViewController {
    let itemManager = ItemManager()
    let tableView = UITableView()

    override func viewDidLoad() {
        super.viewDidLoad()
        tableView.delegate = self
        tableView.dataSource = self
        tableView.register(UITableViewCell.self, forCellReuseIdentifier: "cell")
        view.addSubview(tableView)
        tableView.frame = view.bounds
    }
}

extension ItemListViewController: UITableViewDelegate, UITableViewDataSource {
    func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        return itemManager.items.count
    }

    func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
        let cell = tableView.dequeueReusableCell(withIdentifier: "cell", for: indexPath)
        let item = itemManager.items[indexPath.row]
        cell.textLabel?.text = item.title
        cell.detailTextLabel?.text = item.subtitle
        return cell
    }
}
```

Differences from Junior 1 level:

-   The task requires the implementation of an app with a more complex
    architecture (MVC), including separate classes for the data model and data
    management.
-   The task requires the use of a table view, which is a more complex UI
    component compared to a label or button.
-   The task also requires the implementation of data source and delegate
    methods for the table view, which involve more advanced concepts in iOS
    development.

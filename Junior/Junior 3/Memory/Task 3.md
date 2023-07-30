# Task 3

Task:

Create a custom **`UIViewController`** that presents a list of items fetched
from a remote API. The list should be displayed using a **`UITableView`**, and
each item should have a title and a subtitle. The API endpoint should be called
only once, and the fetched data should be stored and displayed properly.

Additionally, implement a functionality that allows the user to tap on a cell to
view more details about the selected item. The details view should also be a
custom **`UIViewController`** that displays the selected item's title and
subtitle, and should have a back button that returns to the list view.

Solution:

First, we create a **`struct`** to represent the fetched data model:

```swift
struct Item {
    let id: Int
    let title: String
    let subtitle: String
}
```

Next, we create a custom **`UIViewController`** to display the list of items:

```swift
class ItemListViewController: UIViewController {
    private let tableView = UITableView()
    private var items = [Item]()

    override func viewDidLoad() {
        super.viewDidLoad()

        tableView.dataSource = self
        tableView.delegate = self
        tableView.register(UITableViewCell.self, forCellReuseIdentifier: "cell")
        view.addSubview(tableView)

        // Call the API endpoint to fetch the data
        fetchData()
    }

    private func fetchData() {
        // Make the network request to the API endpoint
        // Parse the response data and store it in the items array
        // Reload the table view to display the fetched data
    }
}

extension ItemListViewController: UITableViewDataSource, UITableViewDelegate {
    func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        return items.count
    }

    func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
        let cell = tableView.dequeueReusableCell(withIdentifier: "cell", for: indexPath)
        cell.textLabel?.text = items[indexPath.row].title
        cell.detailTextLabel?.text = items[indexPath.row].subtitle
        return cell
    }

    func tableView(_ tableView: UITableView, didSelectRowAt indexPath: IndexPath) {
        let selectedItem = items[indexPath.row]

        // Instantiate the details view controller and pass the selected item to it
        let detailsViewController = ItemDetailsViewController(item: selectedItem)
        navigationController?.pushViewController(detailsViewController, animated: true)
    }
}
```

Finally, we create a custom **`UIViewController`** to display the details of a
selected item:

```swift
class ItemDetailsViewController: UIViewController {
    private let item: Item
    private let titleLabel = UILabel()
    private let subtitleLabel = UILabel()

    init(item: Item) {
        self.item = item
        super.init(nibName: nil, bundle: nil)
    }

    required init?(coder: NSCoder) {
        fatalError("init(coder:) has not been implemented")
    }

    override func viewDidLoad() {
        super.viewDidLoad()

        titleLabel.text = item.title
        subtitleLabel.text = item.subtitle

        view.addSubview(titleLabel)
        view.addSubview(subtitleLabel)

        // Add constraints to position the title and subtitle labels
    }
}
```

Differences between Junior 2 and Junior 3 level:

-   Junior 3 should be able to optimize the network request to the API endpoint
    by using techniques such as caching and pagination to reduce the memory
    usage and improve the performance of the app.
-   Junior 3 should also have a good understanding of **`UITableView`** and its
    performance implications, and be able to optimize the table view's
    performance by implementing techniques such as cell reuse, estimated row
    heights, and prefetching.

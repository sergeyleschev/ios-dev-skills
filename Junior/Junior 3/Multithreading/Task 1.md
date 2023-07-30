# Task 1

Task: Create a simple iOS app that shows a list of items and updates it every 5
seconds using asyncAfter and @synchronized blocks.

Solution:

1. Create a class that represents the item:

```swift
class Item {
    let name: String
    let price: Int

    init(name: String, price: Int) {
        self.name = name
        self.price = price
    }
}
```

2. Create a ViewController that displays a table view with a list of items:

```swift
class ViewController: UIViewController {
    @IBOutlet weak var tableView: UITableView!

    var items: [Item] = []

    override func viewDidLoad() {
        super.viewDidLoad()
        self.tableView.register(UITableViewCell.self, forCellReuseIdentifier: "cell")
        self.updateItems()
    }

    func updateItems() {
        DispatchQueue.global(qos: .background).asyncAfter(deadline: .now() + 5) { [weak self] in
            guard let self = self else { return }
            @synchronized(self) {
                self.items = self.generateItems()
            }
            DispatchQueue.main.async {
                self.tableView.reloadData()
            }
            self.updateItems()
        }
    }

    func generateItems() -> [Item] {
        let randomNames = ["Apple", "Banana", "Orange", "Lemon", "Peach"]
        return (0..<5).map { Item(name: randomNames[$0], price: Int.random(in: 1...100)) }
    }
}

extension ViewController: UITableViewDataSource {
    func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        return self.items.count
    }

    func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
        let cell = tableView.dequeueReusableCell(withIdentifier: "cell", for: indexPath)
        let item = self.items[indexPath.row]
        cell.textLabel?.text = "\(item.name) - \(item.price) $"
        return cell
    }
}
```

Differences from Junior 2 level:

-   The use of multithreading is more advanced with the use of asyncAfter and
    @synchronized blocks to update the list of items every 5 seconds.
-   The use of weak self to avoid retain cycles.
-   The use of DispatchQueue.global(qos: .background) to perform updates in the
    background thread.
-   The use of DispatchQueue.main.async to update the UI on the main thread.

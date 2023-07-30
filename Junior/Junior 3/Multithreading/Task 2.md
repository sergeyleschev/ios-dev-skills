# Task 2

Task: Create an iOS app that fetches data from an API and displays it in a table
view using URLSession and DispatchGroup.

Solution:

1. Create a model that represents the data:

```swift
struct Item: Decodable {
    let id: Int
    let name: String
    let price: Double
}
```

2. Create a ViewController that displays a table view with the fetched data:

```swift
class ViewController: UIViewController {
    @IBOutlet weak var tableView: UITableView!

    var items: [Item] = []

    override func viewDidLoad() {
        super.viewDidLoad()
        self.tableView.register(UITableViewCell.self, forCellReuseIdentifier: "cell")
        self.fetchData()
    }

    func fetchData() {
        let group = DispatchGroup()
        group.enter()
        URLSession.shared.dataTask(with: URL(string: "https://example.com/items.json")!) { [weak self] data, response, error in
            defer { group.leave() }
            guard let data = data else { return }
            do {
                let items = try JSONDecoder().decode([Item].self, from: data)
                @synchronized(self) {
                    self?.items = items
                }
            } catch {
                print(error.localizedDescription)
            }
        }.resume()
        group.notify(queue: .main) { [weak self] in
            self?.tableView.reloadData()
        }
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

-   The use of URLSession to fetch data from an API.
-   The use of DispatchGroup to wait for multiple tasks to finish.
-   The use of JSONDecoder to decode the fetched data.
-   The use of guard statements to handle errors and prevent unnecessary
    execution of code.
-   The use of weak self to avoid retain cycles.

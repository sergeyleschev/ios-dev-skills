# Task 2

Task: Implement a custom UIViewController that displays a list of items in a
UITableView. The list should be populated from an API endpoint that returns JSON
data. The API request should be made asynchronously, and the view controller
should display a loading indicator while the data is being fetched. Make sure to
handle any potential memory leaks in your implementation.

Solution:

```swift
import UIKit

class ItemListViewController: UIViewController {

    private var items: [Item] = []
    private let tableView = UITableView()
    private let activityIndicatorView = UIActivityIndicatorView(style: .gray)

    override func viewDidLoad() {
        super.viewDidLoad()

        setupTableView()
        setupActivityIndicatorView()
        fetchItems()
    }

    private func setupTableView() {
        view.addSubview(tableView)
        tableView.translatesAutoresizingMaskIntoConstraints = false
        NSLayoutConstraint.activate([
            tableView.leadingAnchor.constraint(equalTo: view.leadingAnchor),
            tableView.trailingAnchor.constraint(equalTo: view.trailingAnchor),
            tableView.topAnchor.constraint(equalTo: view.topAnchor),
            tableView.bottomAnchor.constraint(equalTo: view.bottomAnchor)
        ])

        tableView.register(ItemCell.self, forCellReuseIdentifier: "cell")
        tableView.dataSource = self
    }

    private func setupActivityIndicatorView() {
        view.addSubview(activityIndicatorView)
        activityIndicatorView.translatesAutoresizingMaskIntoConstraints = false
        NSLayoutConstraint.activate([
            activityIndicatorView.centerXAnchor.constraint(equalTo: view.centerXAnchor),
            activityIndicatorView.centerYAnchor.constraint(equalTo: view.centerYAnchor)
        ])

        activityIndicatorView.startAnimating()
    }

    private func fetchItems() {
        let url = URL(string: "https://myapi.com/items")!
        let task = URLSession.shared.dataTask(with: url) { [weak self] (data, response, error) in
            guard let data = data, error == nil else {
                print("Error fetching items: \(error?.localizedDescription ?? "unknown error")")
                return
            }

            do {
                let decoder = JSONDecoder()
                self?.items = try decoder.decode([Item].self, from: data)
                DispatchQueue.main.async {
                    self?.activityIndicatorView.stopAnimating()
                    self?.tableView.reloadData()
                }
            } catch {
                print("Error decoding items: \(error.localizedDescription)")
            }
        }

        task.resume()
    }
}

extension ItemListViewController: UITableViewDataSource {

    func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        return items.count
    }

    func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
        let cell = tableView.dequeueReusableCell(withIdentifier: "cell", for: indexPath) as! ItemCell
        let item = items[indexPath.row]
        cell.configure(with: item)
        return cell
    }
}

class ItemCell: UITableViewCell {

    func configure(with item: Item) {
        // configure cell UI based on item data
    }
}

struct Item: Codable {
    let name: String
    let description: String
    let price: Double
}
```

Differences from Junior 3 level:

-   This task involves fetching data asynchronously from an API endpoint,
    whereas Junior 3 level tasks may have involved loading data from a local
    file or hardcoded data.
-   The Middle 1 level task requires handling potential memory leaks in the
    implementation, which Junior 3 level tasks may not have explicitly required.
-   The implementation uses a custom table view cell class (**`ItemCell`**) to
    configure the cell UI based on the data, which is a step up from Junior 3
    level tasks that may have used the default cell configuration.
-   The implementation uses the **`Codable`** protocol for JSON decoding, which
    is a more advanced and efficient method than manually parsing the JSON data
    as in Junior 3 level tasks.

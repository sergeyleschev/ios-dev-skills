# Task 2

Task: You are given a view controller that displays a list of items fetched from
a server. The view controller has a table view that displays the items and a
button to refresh the list. The view controller also has a network manager
instance that handles the network calls to fetch the items. However, the view
controller is experiencing a memory leak. Find and fix the memory leak.

Solution:

```swift
class MyViewController: UIViewController {

    let tableView = UITableView()
    let refreshButton = UIButton()
    let networkManager = NetworkManager()
    var items = [Item]()

    override func viewDidLoad() {
        super.viewDidLoad()
        configureTableView()
        configureRefreshButton()
        fetchItems()
    }

    func configureTableView() {
        tableView.dataSource = self
        tableView.register(UITableViewCell.self, forCellReuseIdentifier: "cell")
        view.addSubview(tableView)
        tableView.translatesAutoresizingMaskIntoConstraints = false
        tableView.topAnchor.constraint(equalTo: view.topAnchor).isActive = true
        tableView.bottomAnchor.constraint(equalTo: view.bottomAnchor).isActive = true
        tableView.leadingAnchor.constraint(equalTo: view.leadingAnchor).isActive = true
        tableView.trailingAnchor.constraint(equalTo: view.trailingAnchor).isActive = true
    }

    func configureRefreshButton() {
        refreshButton.setTitle("Refresh", for: .normal)
        refreshButton.addTarget(self, action: #selector(fetchItems), for: .touchUpInside)
        view.addSubview(refreshButton)
        refreshButton.translatesAutoresizingMaskIntoConstraints = false
        refreshButton.topAnchor.constraint(equalTo: view.topAnchor, constant: 20).isActive = true
        refreshButton.trailingAnchor.constraint(equalTo: view.trailingAnchor, constant: -20).isActive = true
    }

    @objc func fetchItems() {
        networkManager.fetchItems { [weak self] result in
            switch result {
            case .success(let items):
                self?.items = items
                self?.tableView.reloadData()
            case .failure(let error):
                print(error)
            }
        }
    }
}

extension MyViewController: UITableViewDataSource {
    func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        return items.count
    }

    func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
        let cell = tableView.dequeueReusableCell(withIdentifier: "cell", for: indexPath)
        cell.textLabel?.text = items[indexPath.row].name
        return cell
    }
}
```

Differences from Junior 1 level:

1. The developer is able to identify and fix a memory leak in a more complex app
   architecture.
2. The developer is able to use **`[weak self]`** in a closure to prevent a
   strong reference cycle between the view controller and the network manager.
3. The developer is able to understand the importance of properly managing
   network calls and is able to integrate a network manager instance into the
   view controller.

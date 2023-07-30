# Task 5

Task: Create a screen that displays a list of items using a table view. Each
item should have a title and a subtitle. When a table cell is tapped, show a
detail view with the selected item's title and subtitle. Use auto-layout code to
position the UI elements correctly on different screen sizes.

Solution:

```swift
import UIKit

class ItemListViewController: UIViewController {

    let tableView: UITableView = {
        let tableView = UITableView()
        tableView.translatesAutoresizingMaskIntoConstraints = false
        return tableView
    }()

    let items = [("Item 1", "Subtitle 1"), ("Item 2", "Subtitle 2"), ("Item 3", "Subtitle 3")]

    override func viewDidLoad() {
        super.viewDidLoad()
        view.backgroundColor = .white
        title = "Items"

        view.addSubview(tableView)

        NSLayoutConstraint.activate([
            tableView.topAnchor.constraint(equalTo: view.topAnchor),
            tableView.leadingAnchor.constraint(equalTo: view.leadingAnchor),
            tableView.trailingAnchor.constraint(equalTo: view.trailingAnchor),
            tableView.bottomAnchor.constraint(equalTo: view.bottomAnchor)
        ])

        tableView.dataSource = self
        tableView.delegate = self
        tableView.register(UITableViewCell.self, forCellReuseIdentifier: "Cell")
    }

}

extension ItemListViewController: UITableViewDataSource {

    func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        return items.count
    }

    func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
        let cell = tableView.dequeueReusableCell(withIdentifier: "Cell", for: indexPath)
        cell.textLabel?.text = items[indexPath.row].0
        cell.detailTextLabel?.text = items[indexPath.row].1
        return cell
    }

}

extension ItemListViewController: UITableViewDelegate {

    func tableView(_ tableView: UITableView, didSelectRowAt indexPath: IndexPath) {
        tableView.deselectRow(at: indexPath, animated: true)
        let selectedItem = items[indexPath.row]
        let detailViewController = DetailViewController(title: selectedItem.0, subtitle: selectedItem.1)
        navigationController?.pushViewController(detailViewController, animated: true)
    }

}

class DetailViewController: UIViewController {

    let titleLabel: UILabel = {
        let label = UILabel()
        label.translatesAutoresizingMaskIntoConstraints = false
        return label
    }()

    let subtitleLabel: UILabel = {
        let label = UILabel()
        label.translatesAutoresizingMaskIntoConstraints = false
        return label
    }()

    init(title: String, subtitle: String) {
        super.init(nibName: nil, bundle: nil)
        titleLabel.text = title
        subtitleLabel.text = subtitle
        self.title = "Detail"
    }

    required init?(coder aDecoder: NSCoder) {
        fatalError("init(coder:) has not been implemented")
    }

    override func viewDidLoad() {
        super.viewDidLoad()
        view.backgroundColor = .white

        view.addSubview(titleLabel)
        view.addSubview(subtitleLabel)

        NSLayoutConstraint.activate([
            titleLabel.centerXAnchor.constraint(equalTo: view.centerXAnchor),
            titleLabel.centerYAnchor.constraint(equalTo: view.centerYAnchor, constant: -50),

            subtitleLabel.centerXAnchor.constraint(equalTo: view.centerXAnchor),
            subtitleLabel.topAnchor.constraint(equalTo: titleLabel.bottomAnchor, constant: 20)
        ])
    }

}
```

Differences from Middle level 1:

-   The solution uses auto-layout code instead of storyboard to position the
    table view and the UI elements in the detail view.
-   The solution uses a custom view controller for the detail view, instead of
    presenting a modal view controller.
-   The solution uses a convenience initializer for the detail view controller
    to pass in the title and subtitle.

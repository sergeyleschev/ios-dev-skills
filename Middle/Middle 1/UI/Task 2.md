# Task 2

Task:

Create a screen that displays a list of items with their images, titles, and
subtitles. The items should be scrollable, and the UI should be created entirely
in code using auto layout constraints.

Solution:

```swift
import UIKit

class ViewController: UIViewController {

    let tableView: UITableView = {
        let tableView = UITableView()
        tableView.translatesAutoresizingMaskIntoConstraints = false
        return tableView
    }()

    override func viewDidLoad() {
        super.viewDidLoad()
        view.addSubview(tableView)
        setupTableView()
    }

    func setupTableView() {
        NSLayoutConstraint.activate([
            tableView.topAnchor.constraint(equalTo: view.safeAreaLayoutGuide.topAnchor),
            tableView.leadingAnchor.constraint(equalTo: view.safeAreaLayoutGuide.leadingAnchor),
            tableView.trailingAnchor.constraint(equalTo: view.safeAreaLayoutGuide.trailingAnchor),
            tableView.bottomAnchor.constraint(equalTo: view.safeAreaLayoutGuide.bottomAnchor)
        ])
        tableView.delegate = self
        tableView.dataSource = self
        tableView.register(UITableViewCell.self, forCellReuseIdentifier: "cell")
    }
}

extension ViewController: UITableViewDataSource, UITableViewDelegate {
    func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        return 10
    }

    func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
        let cell = tableView.dequeueReusableCell(withIdentifier: "cell", for: indexPath)
        cell.imageView?.image = UIImage(named: "item\(indexPath.row + 1)")
        cell.textLabel?.text = "Item \(indexPath.row + 1)"
        cell.detailTextLabel?.text = "Subtitle \(indexPath.row + 1)"
        return cell
    }
}
```

Differences from Junior 3 level:

-   The task requires the creation of the UI entirely in code using auto layout
    constraints, which indicates a higher level of proficiency in working with
    auto layout compared to the previous level.
-   The task involves displaying a scrollable list of items with images, titles,
    and subtitles, which requires knowledge of UITableView and its delegate and
    datasource protocols.
-   The task requires the use of the dequeueReusableCell method, which helps
    with performance by reusing table view cells instead of creating new ones
    for each item.

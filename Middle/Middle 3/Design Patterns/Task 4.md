# Task 4

Task:

You are working on a project that requires data to be displayed in a table view.
Implement a Facade pattern to simplify the usage of a data source and delegate
for the table view. The Facade should provide a single method
**`configureTableView(_ tableView: UITableView)`** that will set up the data
source, delegate, and any other necessary properties for the table view.

Solution:

```swift
class TableViewFacade<T: UITableViewCell, U>: NSObject, UITableViewDataSource, UITableViewDelegate {
    private let reuseIdentifier: String
    private let data: [U]
    private let configureCell: (T, U) -> Void
    private let didSelectRow: (U) -> Void

    init(reuseIdentifier: String, data: [U], configureCell: @escaping (T, U) -> Void, didSelectRow: @escaping (U) -> Void) {
        self.reuseIdentifier = reuseIdentifier
        self.data = data
        self.configureCell = configureCell
        self.didSelectRow = didSelectRow
    }

    func configureTableView(_ tableView: UITableView) {
        tableView.register(T.self, forCellReuseIdentifier: reuseIdentifier)
        tableView.dataSource = self
        tableView.delegate = self
    }

    func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        return data.count
    }

    func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
        let cell = tableView.dequeueReusableCell(withIdentifier: reuseIdentifier, for: indexPath) as! T
        let item = data[indexPath.row]
        configureCell(cell, item)
        return cell
    }

    func tableView(_ tableView: UITableView, didSelectRowAt indexPath: IndexPath) {
        let item = data[indexPath.row]
        didSelectRow(item)
    }
}

struct Person {
    let name: String
    let age: Int
    // other properties
}

class PersonTableViewCell: UITableViewCell {
    func configure(with person: Person) {
        // configure cell
    }
}

class ViewController: UIViewController {
    private let people = [Person(name: "John", age: 30), Person(name: "Jane", age: 25), Person(name: "Bob", age: 40)]

    private lazy var tableViewFacade = TableViewFacade<PersonTableViewCell, Person>(
        reuseIdentifier: "PersonCell",
        data: people,
        configureCell: { cell, person in
            cell.configure(with: person)
        },
        didSelectRow: { person in
            print("\(person.name) was selected")
        }
    )

    private let tableView = UITableView()

    override func viewDidLoad() {
        super.viewDidLoad()
        tableView.frame = view.bounds
        view.addSubview(tableView)
        tableViewFacade.configureTableView(tableView)
    }
}
```

Differences that indicate the development of the developer to the level of
middle 3:

-   Proficient knowledge of Design Patterns, especially the Facade pattern, and
    its application in simplifying the usage of complex systems.
-   Ability to use generic programming to create reusable components that work
    with different types of data.
-   Strong understanding of the UIKit framework and its components, such as
    UITableView and UITableViewCell.
-   Good knowledge of object-oriented programming and principles, such as
    inheritance and polymorphism.

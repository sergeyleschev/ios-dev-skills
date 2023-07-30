# Task 1

Task: Given the following code snippet, identify and fix any potential memory
leaks:

```swift
class ViewController: UIViewController {

    var data: [String] = []

    override func viewDidLoad() {
        super.viewDidLoad()

        fetchData { [weak self] result in
            guard let self = self else { return }

            self.data = result
            self.tableView.reloadData()
        }
    }

    func fetchData(completion: @escaping ([String]) -> Void) {
        let url = URL(string: "https://example.com/data.json")!
        URLSession.shared.dataTask(with: url) { data, _, _ in
            guard let data = data,
                  let json = try? JSONSerialization.jsonObject(with: data, options: []) as? [String: Any],
                  let items = json?["items"] as? [String]
            else {
                completion([])
                return
            }

            completion(items)
        }.resume()
    }

    lazy var tableView: UITableView = {
        let tableView = UITableView()
        // configure table view here
        return tableView
    }()

    override func viewDidLayoutSubviews() {
        super.viewDidLayoutSubviews()
        tableView.frame = view.bounds
    }

    deinit {
        print("Deallocated")
    }
}
```

Solution: The potential memory leak in the given code is due to the strong
reference cycle created between the closure and the **`ViewController`**
instance. To fix this, we can use a **`weak`** reference to the
**`ViewController`** inside the closure and then use a **`guard`** statement to
make sure the instance is not **`nil`**. Also, we can use **`unowned`**
reference to **`self`** inside the closure when we are sure that the instance is
not **`nil`**.

```swift
class ViewController: UIViewController {

    var data: [String] = []

    override func viewDidLoad() {
        super.viewDidLoad()

        fetchData { [weak self] result in
            guard let self = self else { return }

            self.data = result
            self.tableView.reloadData()
        }
    }

    func fetchData(completion: @escaping ([String]) -> Void) {
        let url = URL(string: "https://example.com/data.json")!
        URLSession.shared.dataTask(with: url) { [weak self] data, _, _ in
            guard let self = self,
                  let data = data,
                  let json = try? JSONSerialization.jsonObject(with: data, options: []) as? [String: Any],
                  let items = json?["items"] as? [String]
            else {
                completion([])
                return
            }

            completion(items)
        }.resume()
    }

    lazy var tableView: UITableView = {
        let tableView = UITableView()
        // configure table view here
        return tableView
    }()

    override func viewDidLayoutSubviews() {
        super.viewDidLayoutSubviews()
        tableView.frame = view.bounds
    }

    deinit {
        print("Deallocated")
    }
}
```

Difference from Junior 3 level: The difference between the Junior 3 level and
the Middle 1 level is that the Middle 1 level should be able to identify
potential memory leaks in more complex code structures and have a deeper
understanding of ARC (Automatic Reference Counting) and how to use **`weak`**
and **`unowned`** references to avoid strong reference cycles. In addition, the
Middle 1 level should be able to recognize and use memory management tools such
as Instruments to identify memory leaks and optimize memory usage in more
complex projects.

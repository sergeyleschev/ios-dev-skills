# Task 4

Task: Create an iOS app that displays a list of names in a UITableView. The
names should be loaded asynchronously from a JSON file using URLSession.

Solution:

1. Create a data model to represent the names:

```swift
struct Name {
    let first: String
    let last: String

    init(json: [String: Any]) {
        self.first = json["first"] as? String ?? ""
        self.last = json["last"] as? String ?? ""
    }
}
```

2. Create a ViewController with a UITableView and an array to hold the names:

```swift
class ViewController: UIViewController, UITableViewDataSource {
    @IBOutlet weak var tableView: UITableView!

    var names = [Name]()

    override func viewDidLoad() {
        super.viewDidLoad()
        self.loadNames()
    }

    func loadNames() {
        guard let url = URL(string: "https://example.com/names.json") else { return }
        URLSession.shared.dataTask(with: url) { (data, response, error) in
            guard let data = data else { return }
            do {
                if let json = try JSONSerialization.jsonObject(with: data, options: []) as? [[String: Any]] {
                    self.names = json.map { Name(json: $0) }
                    DispatchQueue.main.async {
                        self.tableView.reloadData()
                    }
                }
            } catch {
                print(error.localizedDescription)
            }
        }.resume()
    }

    func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        return self.names.count
    }

    func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
        let cell = tableView.dequeueReusableCell(withIdentifier: "NameCell", for: indexPath)
        let name = self.names[indexPath.row]
        cell.textLabel?.text = "\(name.first) \(name.last)"
        return cell
    }
}

```

Differences from Junior 2 level:

-   The use of URLSession to load data asynchronously from a URL.
-   The use of a data model to represent the data.
-   The use of JSONSerialization to parse JSON data.
-   The use of DispatchQueue.main.async to update the UI on the main thread.

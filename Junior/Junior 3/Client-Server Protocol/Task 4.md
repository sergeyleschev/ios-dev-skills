# Task 4

Task: You need to implement a network request to get data from an API that
returns a JSON response containing an array of objects. The request must be made
using the URLSession class, and the JSON response must be parsed using the
JSONDecoder class. Once the data has been successfully retrieved and parsed, you
should display the information in a table view, where each row corresponds to an
object in the JSON response. Each row should display the name and description
fields of the object.

Solution:

```swift
struct Item: Decodable {
    let name: String
    let description: String
}

class ViewController: UIViewController, UITableViewDelegate, UITableViewDataSource {
    var items: [Item] = []
    @IBOutlet weak var tableView: UITableView!

    override func viewDidLoad() {
        super.viewDidLoad()
        tableView.delegate = self
        tableView.dataSource = self

        let url = URL(string: "https://example.com/items")!
        let task = URLSession.shared.dataTask(with: url) { data, response, error in
            guard let data = data, error == nil else {
                print("Error: \(error!)")
                return
            }

            do {
                self.items = try JSONDecoder().decode([Item].self, from: data)
                DispatchQueue.main.async {
                    self.tableView.reloadData()
                }
            } catch {
                print("Error: \(error)")
            }
        }
        task.resume()
    }

    func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        return items.count
    }

    func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
        let cell = tableView.dequeueReusableCell(withIdentifier: "Cell", for: indexPath)
        let item = items[indexPath.row]
        cell.textLabel?.text = item.name
        cell.detailTextLabel?.text = item.description
        return cell
    }
}
```

Differences from Junior 2:

-   The task now involves using a table view to display the parsed JSON data.
-   The implementation now includes the UITableViewDelegate and
    UITableViewDataSource protocols.
-   The implementation now handles the network request using a closure-based
    approach using the URLSession class.
-   The implementation uses DispatchQueue.main.async to update the UI on the
    main thread.

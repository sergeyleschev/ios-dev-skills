# Task 2

Task: Implement a GET request to an API endpoint that returns a list of JSON
objects, and display the data in a table view with custom cells.

Solution:

```swift
import UIKit

class ViewController: UIViewController, UITableViewDelegate, UITableViewDataSource {

    @IBOutlet weak var tableView: UITableView!

    var data: [DataObject] = []

    override func viewDidLoad() {
        super.viewDidLoad()
        // Do any additional setup after loading the view.

        getData()
    }

    func getData() {
        guard let url = URL(string: "https://jsonplaceholder.typicode.com/posts") else {
            print("Invalid URL")
            return
        }

        URLSession.shared.dataTask(with: url) { (data, response, error) in
            if let error = error {
                print("Error: \(error.localizedDescription)")
                return
            }

            guard let httpResponse = response as? HTTPURLResponse, httpResponse.statusCode == 200 else {
                print("Invalid response")
                return
            }

            guard let data = data else {
                print("No data received")
                return
            }

            do {
                let decoder = JSONDecoder()
                self.data = try decoder.decode([DataObject].self, from: data)

                DispatchQueue.main.async {
                    self.tableView.reloadData()
                }
            } catch {
                print("Error: \(error.localizedDescription)")
            }
        }.resume()
    }

    func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        return data.count
    }

    func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
        let cell = tableView.dequeueReusableCell(withIdentifier: "CustomCell", for: indexPath) as! CustomCell
        cell.titleLabel.text = data[indexPath.row].title
        cell.bodyLabel.text = data[indexPath.row].body
        return cell
    }

}

struct DataObject: Codable {
    let userId: Int
    let id: Int
    let title: String
    let body: String
}

class CustomCell: UITableViewCell {
    @IBOutlet weak var titleLabel: UILabel!
    @IBOutlet weak var bodyLabel: UILabel!
}

```

Differences from Junior 1 level:

-   The implementation includes the use of Codable protocol to parse JSON data.
-   The use of asynchronous networking with URLSession.
-   The implementation of a custom table view cell.

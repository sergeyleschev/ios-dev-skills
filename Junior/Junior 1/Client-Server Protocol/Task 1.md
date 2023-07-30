# Task 1

Task: You need to create an iOS app that retrieves JSON data from an API
endpoint and displays the data in a UITableView. The API endpoint is:
**https://jsonplaceholder.typicode.com/users**

Solution:

1. Create a new Xcode project and select "Single View App" template.
2. Open ViewController.swift and add the following code:

```swift
import UIKit

class ViewController: UIViewController, UITableViewDelegate, UITableViewDataSource {

    @IBOutlet weak var tableView: UITableView!

    var users: [User] = []

    override func viewDidLoad() {
        super.viewDidLoad()

        tableView.delegate = self
        tableView.dataSource = self

        getData()
    }

    func getData() {
        guard let url = URL(string: "https://jsonplaceholder.typicode.com/users") else { return }

        URLSession.shared.dataTask(with: url) { data, response, error in
            guard let data = data else { return }

            do {
                self.users = try JSONDecoder().decode([User].self, from: data)
                DispatchQueue.main.async {
                    self.tableView.reloadData()
                }
            } catch {
                print(error.localizedDescription)
            }
        }.resume()
    }

    func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        return users.count
    }

    func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
        let cell = tableView.dequeueReusableCell(withIdentifier: "cell", for: indexPath)

        let user = users[indexPath.row]
        cell.textLabel?.text = user.name

        return cell
    }

}

```

3. Create a new file called "User.swift" and add the following code:

```swift
import Foundation

struct User: Codable {
    let id: Int
    let name: String
    let username: String
    let email: String
    let phone: String
    let website: String
    let address: Address
    let company: Company
}

struct Address: Codable {
    let street: String
    let suite: String
    let city: String
    let zipcode: String
    let geo: Geo
}

struct Geo: Codable {
    let lat: String
    let lng: String
}

struct Company: Codable {
    let name: String
    let catchPhrase: String
    let bs: String
}

```

4. Open Main.storyboard and add a UITableView to the ViewController. Set the
   UITableView's dataSource and delegate to the ViewController.
5. Create a UITableViewCell with a reuseIdentifier of "cell". Add a UILabel to
   the cell and set its tag to 1.
6. Run the app and the JSON data should be displayed in the UITableView.

Note: This code uses URLSession to make a network request and decode the JSON
response using Codable. It also uses GCD to update the UI on the main thread.

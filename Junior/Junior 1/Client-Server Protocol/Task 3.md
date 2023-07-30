# Task 3

Task: You need to create an iOS app that retrieves JSON data from an API
endpoint and displays the data in a UITableView. The API endpoint is:
**https://jsonplaceholder.typicode.com/posts**

Solution:

1. Create a new Xcode project and select "Single View App" template.
2. Open ViewController.swift and add the following code:

```swift
import UIKit

class ViewController: UIViewController, UITableViewDelegate, UITableViewDataSource {

    @IBOutlet weak var tableView: UITableView!

    var posts: [Post] = []

    override func viewDidLoad() {
        super.viewDidLoad()

        tableView.delegate = self
        tableView.dataSource = self

        getData()
    }

    func getData() {
        guard let url = URL(string: "https://jsonplaceholder.typicode.com/posts") else { return }

        URLSession.shared.dataTask(with: url) { data, response, error in
            guard let data = data else { return }

            do {
                self.posts = try JSONDecoder().decode([Post].self, from: data)
                DispatchQueue.main.async {
                    self.tableView.reloadData()
                }
            } catch {
                print(error.localizedDescription)
            }
        }.resume()
    }

    func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        return posts.count
    }

    func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
        let cell = tableView.dequeueReusableCell(withIdentifier: "cell", for: indexPath)

        let post = posts[indexPath.row]
        cell.textLabel?.text = post.title
        cell.detailTextLabel?.text = post.body

        return cell
    }

}

struct Post: Codable {
    let userId: Int
    let id: Int
    let title: String
    let body: String
}

```

3. Open Main.storyboard and add a UITableView to the ViewController. Set the
   UITableView's dataSource, delegate and cell prototype to the ViewController.
4. Create a UITableViewCell with a reuseIdentifier of "cell". Add a UILabel for
   the title and another UILabel for the body of the post.
5. Run the app and the JSON data should be displayed in the UITableView.

Note: This code uses URLSession to make a network request and decode the JSON
response using Codable. The table view's dataSource and delegate are set to the
ViewController, and the cellForRowAt method is used to populate the cells with
the data from the JSON response.

# Task 4

Task: Create a simple iOS app that retrieves a list of users from an API
endpoint and displays it in a table view. Implement the view layer using UIKit
and the MVVM architecture pattern. Use URLSession for networking.

Solution:

1. Create a new Xcode project and select the "Single View App" template.
2. Open the ViewController.swift file and delete all the boilerplate code.
3. Create a new file called "UserViewModel.swift" and add the following code:

```swift
import Foundation

class UserViewModel {

    private let url = URL(string: "https://jsonplaceholder.typicode.com/users")!
    private var users = [User]()

    func getUsers(completion: @escaping () -> Void) {
        URLSession.shared.dataTask(with: url) { [weak self] data, _, error in
            guard let data = data else { return }
            do {
                self?.users = try JSONDecoder().decode([User].self, from: data)
                completion()
            } catch {
                print(error.localizedDescription)
            }
        }.resume()
    }

    func numberOfUsers() -> Int {
        return users.count
    }

    func user(at index: Int) -> User {
        return users[index]
    }

}

struct User: Decodable {
    let id: Int
    let name: String
    let username: String
    let email: String
    let phone: String
    let website: String
    let company: Company
}

struct Company: Decodable {
    let name: String
    let catchPhrase: String
    let bs: String
}
```

4. In the ViewController.swift file, add the following code:

```swift
import UIKit

class ViewController: UIViewController {

    @IBOutlet weak var tableView: UITableView!

    private let viewModel = UserViewModel()

    override func viewDidLoad() {
        super.viewDidLoad()
        // Do any additional setup after loading the view.
        viewModel.getUsers { [weak self] in
            DispatchQueue.main.async {
                self?.tableView.reloadData()
            }
        }
    }

}

extension ViewController: UITableViewDataSource {

    func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        return viewModel.numberOfUsers()
    }

    func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
        let cell = tableView.dequeueReusableCell(withIdentifier: "cell", for: indexPath)
        let user = viewModel.user(at: indexPath.row)
        cell.textLabel?.text = user.name
        cell.detailTextLabel?.text = user.company.name
        return cell
    }

}
```

5. In the Main.storyboard file, drag a UITableView to the view controller and
   set its delegate and data source to the view controller. Also, give it a
   reuse identifier of "cell".
6. Build and run the app, and verify that the list of users is displayed in the
   table view.

Differences from previous levels:

-   This task introduces the MVVM architecture pattern, which is commonly used
    in iOS app development to separate the responsibilities of the view, model,
    and view model layers.
-   The code uses the URLSession API to retrieve data from an API endpoint,
    which is a more advanced technique than using static data or simple file
    I/O.
-   The code also introduces the concept of asynchronous programming using
    completion handlers and DispatchQueue.main.async. This is a more advanced
    topic than synchronous programming and requires a good understanding of
    concurrency and thread safety.

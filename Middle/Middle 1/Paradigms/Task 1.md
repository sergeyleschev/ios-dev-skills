# Task 1

Task: Create a simple iOS app that fetches a list of users from an API and
displays them in a table view using RxSwift.

Solution:

1. Create a model to represent a User:

```swift
struct User {
    let id: Int
    let name: String
    let email: String
}
```

2. Create a **`UserAPI`** class that fetches a list of users from an API:

```swift
import RxSwift

class UserAPI {
    static func getUsers() -> Observable<[User]> {
        let url = URL(string: "https://jsonplaceholder.typicode.com/users")!
        let request = URLRequest(url: url)
        return URLSession.shared.rx.json(request: request)
            .map { json -> [User] in
                guard let jsonArray = json as? [[String: Any]] else { return [] }
                return jsonArray.compactMap { json in
                    guard let id = json["id"] as? Int,
                          let name = json["name"] as? String,
                          let email = json["email"] as? String else {
                        return nil
                    }
                    return User(id: id, name: name, email: email)
                }
            }
    }
}
```

3. Create a view controller that displays the list of users in a table view:

```swift
import UIKit
import RxSwift
import RxCocoa

class UserListViewController: UIViewController {

    @IBOutlet weak var tableView: UITableView!

    let disposeBag = DisposeBag()
    var users: [User] = []

    override func viewDidLoad() {
        super.viewDidLoad()

        UserAPI.getUsers()
            .subscribe(onNext: { [weak self] users in
                self?.users = users
                self?.tableView.reloadData()
            })
            .disposed(by: disposeBag)

        tableView.dataSource = self
    }
}

extension UserListViewController: UITableViewDataSource {
    func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        return users.count
    }

    func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
        let cell = tableView.dequeueReusableCell(withIdentifier: "UserCell", for: indexPath)
        let user = users[indexPath.row]
        cell.textLabel?.text = user.name
        cell.detailTextLabel?.text = user.email
        return cell
    }
}
```

4. Set up the view controller in the storyboard and assign it to the initial
   view controller. Add a table view to the view controller and set its data
   source to the view controller.

Differences between Junior 3 and Middle 1:

-   Knowledge of FRP concepts and tools (in this case, RxSwift) is required for
    the Middle 1 level task.
-   The task involves integrating an external API and displaying the data in a
    table view, which requires knowledge of network requests and table view data
    sources.
-   The code is organized into separate classes (model, API, view controller) to
    improve maintainability and readability.

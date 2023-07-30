# Task 5

Task: Develop a feature that integrates with an external API to retrieve data
and display it in a UITableView. Use RxSwift to handle the asynchronous requests
and MVVM architecture to structure the code.

Solution:

```swift
import UIKit
import RxSwift
import RxCocoa

struct User: Codable {
    let id: Int
    let name: String
}

class UsersViewModel {
    private let disposeBag = DisposeBag()
    private let usersSubject = PublishSubject<[User]>()

    var users: Driver<[User]> {
        return usersSubject.asDriver(onErrorJustReturn: [])
    }

    func fetchUsers() {
        guard let url = URL(string: "https://jsonplaceholder.typicode.com/users") else {
            return
        }

        URLSession.shared.rx
            .json(url: url)
            .map { json -> [User] in
                guard let users = try? JSONDecoder().decode([User].self, from: json as! Data) else {
                    return []
                }
                return users
            }
            .bind(to: usersSubject)
            .disposed(by: disposeBag)
    }
}

class UsersViewController: UIViewController {
    private let tableView = UITableView()
    private let viewModel = UsersViewModel()
    private let disposeBag = DisposeBag()

    override func viewDidLoad() {
        super.viewDidLoad()
        setupTableView()
        setupBindings()
        viewModel.fetchUsers()
    }

    private func setupTableView() {
        view.addSubview(tableView)
        tableView.frame = view.bounds
        tableView.register(UITableViewCell.self, forCellReuseIdentifier: "cell")
    }

    private func setupBindings() {
        viewModel.users
            .drive(tableView.rx.items(cellIdentifier: "cell")) { index, model, cell in
                cell.textLabel?.text = model.name
            }
            .disposed(by: disposeBag)
    }
}
```

Differences from Middle 3 level:

-   Integration with external API and handling of asynchronous requests using
    RxSwift
-   Use of **`Driver`** to bind data to UI elements in a reactive way
-   Additional focus on separation of concerns with the **`UsersViewModel`**
    class responsible for retrieving and transforming data, while the
    **`UsersViewController`** is responsible for UI presentation.

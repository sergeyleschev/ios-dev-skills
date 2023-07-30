# Task 2

Task: Write a simple application that fetches data from an API and displays it
on the screen. However, if the API request fails, display an error message to
the user. Use a reactive programming approach to handle the API request and
response.

Solution:

```swift
import UIKit
import RxSwift
import RxCocoa

class ViewController: UIViewController {

    @IBOutlet weak var tableView: UITableView!
    @IBOutlet weak var errorMessageLabel: UILabel!

    let disposeBag = DisposeBag()
    let viewModel = ViewModel()

    override func viewDidLoad() {
        super.viewDidLoad()

        viewModel.items
            .bind(to: tableView.rx.items(cellIdentifier: "cell")) { (index, item, cell) in
                cell.textLabel?.text = item.title
            }
            .disposed(by: disposeBag)

        viewModel.errorMessage
            .bind(to: errorMessageLabel.rx.text)
            .disposed(by: disposeBag)
    }
}

class ViewModel {

    let items = BehaviorRelay<[Item]>(value: [])
    let errorMessage = PublishSubject<String>()
    let disposeBag = DisposeBag()

    init() {
        let url = URL(string: "https://jsonplaceholder.typicode.com/posts")!
        let request = URLRequest(url: url)

        URLSession.shared.rx.response(request: request)
            .map { (response, data) -> [Item] in
                guard (200..<300) ~= response.statusCode else {
                    throw NSError(domain: "", code: response.statusCode, userInfo: nil)
                }
                return try JSONDecoder().decode([Item].self, from: data)
            }
            .subscribe(onNext: { [weak self] items in
                self?.items.accept(items)
            }, onError: { [weak self] error in
                self?.errorMessage.onNext("Error: \(error.localizedDescription)")
            })
            .disposed(by: disposeBag)
    }
}

struct Item: Decodable {
    let title: String
}
```

The key difference between this task and the previous one is the use of
**`BehaviorRelay`** and **`PublishSubject`** in the **`ViewModel`**.
**`BehaviorRelay`** is a type of **`Observable`** that always has a value and
emits that value to any new subscribers, making it useful for storing and
exposing the state of the application. **`PublishSubject`** is a type of
**`Observable`** that emits any new values to its subscribers, making it useful
for displaying error messages to the user.

In the **`ViewModel`**, we use **`BehaviorRelay`** to store the items fetched
from the API and expose them to the **`ViewController`** via the **`items`**
property. We also use **`PublishSubject`** to emit any error messages that occur
during the API request and response, and expose them to the **`ViewController`**
via the **`errorMessage`** property.

In the **`ViewController`**, we use **`bind(to:)`** to bind the **`items`** and
**`errorMessage`** properties of the **`ViewModel`** to the **`tableView`** and
**`errorMessageLabel`** views, respectively. This ensures that any changes to
the state of the **`ViewModel`** are automatically reflected in the UI.

Overall, this task tests the developer's ability to use reactive programming
concepts to handle API requests and responses, as well as their ability to
handle errors and display error messages to the user.

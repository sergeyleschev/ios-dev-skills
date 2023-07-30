# Task 2

Task:

Implement a simple search feature for a list of items using FRP. The search bar
should allow the user to search for items in real-time as they type. The list
should be displayed below the search bar and should update dynamically as the
user types.

Requirements:

1. The list of items can be an array of strings or any other simple data type.
2. Use the **`BehaviorRelay`** class from RxSwift to represent the search query.
3. Use the **`filter`** operator from RxSwift to filter the list of items based
   on the search query.
4. Use a table view or collection view to display the list of filtered items.

Solution:

```swift
import UIKit
import RxSwift
import RxCocoa

class SearchViewController: UIViewController {

    @IBOutlet weak var searchBar: UISearchBar!
    @IBOutlet weak var tableView: UITableView!

    let items: [String] = ["Apple", "Banana", "Cherry", "Durian", "Eggplant", "Fig"]
    let disposeBag = DisposeBag()

    override func viewDidLoad() {
        super.viewDidLoad()

        let searchQuery = BehaviorRelay(value: "")

        searchBar.rx.text
            .orEmpty
            .bind(to: searchQuery)
            .disposed(by: disposeBag)

        searchQuery.asObservable()
            .map { query in
                self.items.filter { item in
                    query.isEmpty || item.lowercased().contains(query.lowercased())
                }
            }
            .bind(to: tableView.rx.items(cellIdentifier: "Cell")) { index, element, cell in
                cell.textLabel?.text = element
            }
            .disposed(by: disposeBag)
    }
}
```

Differences from the Middle 2 level solution:

1. Use of **`BehaviorRelay`** to represent the search query instead of a regular
   **`PublishSubject`** or **`BehaviorSubject`**.
2. Use of the **`orEmpty`** operator on the search bar's **`rx.text`**
   observable to prevent crashes if the search bar's text is **`nil`**.
3. Use of the **`bind(to:)`** operator to bind the search query observable to
   the table view's **`rx.items`** observable, instead of manually updating the
   table view's data source.

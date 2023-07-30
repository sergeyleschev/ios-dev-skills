# Task 1

Task: Implement a simple iOS app that displays a list of items retrieved from an
API. When the user taps on an item, display a detail view with more information
about the item. Use FRP to handle user interactions and data retrieval.

Solution:

```swift
import UIKit
import RxSwift
import RxCocoa

class ItemListViewController: UIViewController {

    let disposeBag = DisposeBag()

    var viewModel: ItemListViewModel!

    @IBOutlet weak var tableView: UITableView!

    override func viewDidLoad() {
        super.viewDidLoad()

        viewModel = ItemListViewModel()

        viewModel.items
            .drive(tableView.rx.items(cellIdentifier: "Cell")) { _, item, cell in
                cell.textLabel?.text = item.title
            }
            .disposed(by: disposeBag)

        tableView.rx.modelSelected(Item.self)
            .bind(to: viewModel.selectedItem)
            .disposed(by: disposeBag)

    }
}

class ItemDetailViewController: UIViewController {

    let disposeBag = DisposeBag()

    var viewModel: ItemDetailViewModel!

    @IBOutlet weak var titleLabel: UILabel!
    @IBOutlet weak var descriptionLabel: UILabel!

    override func viewDidLoad() {
        super.viewDidLoad()

        viewModel = ItemDetailViewModel()

        viewModel.title
            .drive(titleLabel.rx.text)
            .disposed(by: disposeBag)

        viewModel.description
            .drive(descriptionLabel.rx.text)
            .disposed(by: disposeBag)
    }
}

struct Item {
    let title: String
    let description: String
}

class ItemListViewModel {

    let items: Driver<[Item]>
    let selectedItem = PublishRelay<Item>()

    init() {

        items = Observable<[Item]>.just([
            Item(title: "Item 1", description: "This is item 1"),
            Item(title: "Item 2", description: "This is item 2"),
            Item(title: "Item 3", description: "This is item 3")
        ])
        .asDriver(onErrorJustReturn: [])

    }
}

class ItemDetailViewModel {

    let title: Driver<String>
    let description: Driver<String>

    init() {

        let item = BehaviorRelay<Item?>(value: nil)

        title = item.asDriver()
            .map { $0?.title ?? "" }

        description = item.asDriver()
            .map { $0?.description ?? "" }

        selectedItem
            .bind(to: item)
            .disposed(by: disposeBag)

    }
}
```

Differences from Middle 1 level:

-   Use of more advanced RxSwift concepts such as **`BehaviorRelay`**,
    **`PublishRelay`** and **`Driver`**.
-   Ability to create more complex view models that handle user interactions and
    data retrieval using FRP.
-   Ability to structure code in a more modular and maintainable way by
    separating concerns between view controllers and view models.

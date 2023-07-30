# Task 2

Task: Create an app that retrieves a list of articles from a remote API and
displays them in a table view. Implement the Observer pattern to handle updates
to the articles list in real-time.

Solution:

```swift
import UIKit

class ArticleListViewController: UIViewController {
    private let tableView = UITableView()
    private var articles: [Article] = []
    private var observer: Observer?

    override func viewDidLoad() {
        super.viewDidLoad()

        // Set up table view
        view.addSubview(tableView)
        tableView.frame = view.bounds
        tableView.dataSource = self
        tableView.register(UITableViewCell.self, forCellReuseIdentifier: "Cell")

        // Set up observer
        let articleService = ArticleService()
        observer = ArticleListObserver(articleService: articleService)
        observer?.startObserving { [weak self] newArticles in
            self?.articles = newArticles
            self?.tableView.reloadData()
        }
    }
}

extension ArticleListViewController: UITableViewDataSource {
    func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        return articles.count
    }

    func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
        let cell = tableView.dequeueReusableCell(withIdentifier: "Cell", for: indexPath)
        cell.textLabel?.text = articles[indexPath.row].title
        return cell
    }
}

class ArticleService {
    var articles: [Article] = []

    func fetchArticles(completion: @escaping ([Article]) -> Void) {
        // Make API call to fetch articles
        // ...
        // Once we have the articles, store them and call the completion block
        articles = fetchedArticles
        completion(articles)
    }
}

protocol Observer {
    func startObserving(completion: @escaping ([Article]) -> Void)
    func stopObserving()
}

class ArticleListObserver: Observer {
    private let articleService: ArticleService
    private var timer: Timer?

    init(articleService: ArticleService) {
        self.articleService = articleService
    }

    func startObserving(completion: @escaping ([Article]) -> Void) {
        timer = Timer.scheduledTimer(withTimeInterval: 5, repeats: true) { [weak self] _ in
            self?.articleService.fetchArticles { articles in
                completion(articles)
            }
        }
    }

    func stopObserving() {
        timer?.invalidate()
        timer = nil
    }
}

struct Article {
    let title: String
    let body: String
}
```

Differences between Middle 1 and Middle 2 level:

At the Middle 2 level, the developer should be able to:

-   Implement the Observer pattern in a more complex and customizable way, like
    in the example above where the observer is a separate object that can be
    started and stopped.
-   Handle more complex data models and API calls.
-   Implement more advanced UI features like custom table view cells or
    pagination.
-   Have a better understanding of performance optimization techniques and
    memory management.

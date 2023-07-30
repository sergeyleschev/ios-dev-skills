# Task 2

Task: Implement a pull-to-refresh feature that retrieves the latest news
articles from the JSON API.

Solution:

```swift
lazy var refreshControl: UIRefreshControl = {
    let control = UIRefreshControl()
    control.addTarget(self, action: #selector(refreshNewsArticles), for: .valueChanged)
    return control
}()

override func viewDidLoad() {
    super.viewDidLoad()
    tableView.addSubview(refreshControl)
}

@objc func refreshNewsArticles() {
    fetchNewsArticles()
    refreshControl.endRefreshing()
}

```

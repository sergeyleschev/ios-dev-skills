# Task 1

Task: Implement a search functionality in the news app.

You have been given a news app that displays the latest news headlines from a
JSON API. Your task is to implement a search functionality that allows users to
search for news articles by keyword.

Requirements:

-   The search bar should be placed in the app's navigation bar.
-   When a user enters a search term and taps the search button, the app should
    query the API for articles containing that term.
-   The search results should be displayed in a separate table view controller,
    with each cell displaying the article's title and thumbnail image.
-   Tapping a search result cell should display the full article in a detail
    view controller.

Hints:

-   Use the URLSession API to query the API and parse the JSON response.
-   Consider using a separate view controller for the search results to keep the
    code organized.
-   You can use a third-party library like Kingfisher to download and cache the
    article thumbnail images.

Solution:

1. Create a new view controller for the search results.

```swift
class SearchResultsViewController: UITableViewController {
    var articles: [Article] = []

    override func viewDidLoad() {
        super.viewDidLoad()
        tableView.register(ArticleCell.self, forCellReuseIdentifier: "ArticleCell")
    }

    // MARK: - Table view data source

    override func numberOfSections(in tableView: UITableView) -> Int {
        return 1
    }

    override func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        return articles.count
    }

    override func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
        let cell = tableView.dequeueReusableCell(withIdentifier: "ArticleCell", for: indexPath) as! ArticleCell
        cell.configure(with: articles[indexPath.row])
        return cell
    }

    // MARK: - Table view delegate

    override func tableView(_ tableView: UITableView, didSelectRowAt indexPath: IndexPath) {
        let article = articles[indexPath.row]
        let detailVC = ArticleDetailViewController(article: article)
        navigationController?.pushViewController(detailVC, animated: true)
    }
}
```

2. Implement the search functionality in the main view controller.

```swift
class NewsViewController: UITableViewController {
    var articles: [Article] = []
    let searchController = UISearchController(searchResultsController: SearchResultsViewController())

    override func viewDidLoad() {
        super.viewDidLoad()
        tableView.register(ArticleCell.self, forCellReuseIdentifier: "ArticleCell")
        setupSearchController()
        fetchArticles()
    }

    func setupSearchController() {
        searchController.searchResultsUpdater = self
        searchController.obscuresBackgroundDuringPresentation = false
        searchController.searchBar.placeholder = "Search News"
        navigationItem.searchController = searchController
        definesPresentationContext = true
    }

    func fetchArticles() {
        // fetch articles from API and populate articles array
    }
}

extension NewsViewController: UISearchResultsUpdating {
    func updateSearchResults(for searchController: UISearchController) {
        guard let searchTerm = searchController.searchBar.text?.trimmingCharacters(in: .whitespacesAndNewlines), !searchTerm.isEmpty else {
            return
        }

        let searchResultsVC = searchController.searchResultsController as! SearchResultsViewController
        searchResultsVC.articles = articles.filter { $0.title.lowercased().contains(searchTerm.lowercased()) }
        searchResultsVC.tableView.reloadData()
    }
}
```

Differences from Junior 2 level:

-   Implementing a search functionality requires a higher understanding of
    asynchronous programming using URLSession and parsing JSON responses.
-   Handling multiple view controllers and their interactions, such as pushing a
    detail view controller on selection of a cell in the search results.
-   Using third-party libraries like Kingfisher to download and cache images.

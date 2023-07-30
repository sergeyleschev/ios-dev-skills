# Task 3

Task: Add a search bar to the news articles table view that filters articles
based on the user's search query.

Solution:

```swift
var filteredNewsArticles: [NewsArticle] = []
var isSearching = false

func filterNewsArticles(for searchText: String) {
    filteredNewsArticles = newsArticles.filter { article in
        article.title.localizedCaseInsensitiveContains(searchText)
    }
    tableView.reloadData()
}

func searchBar(_ searchBar: UISearchBar, textDidChange searchText: String) {
    isSearching = !searchText.isEmpty
    filterNewsArticles(for: searchText)
}

func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
    return isSearching ? filteredNewsArticles.count : newsArticles.count
}

func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
    let article = isSearching ? filteredNewsArticles[indexPath.row] : newsArticles[indexPath.row]
    // configure and return the cell
}

```

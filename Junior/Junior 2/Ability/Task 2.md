# Task 2

Task: Implement pagination for the news articles fetched from the JSON API. The
API returns a maximum of 20 articles per page, and you need to load the next
page of articles when the user scrolls to the bottom of the table view.

Solution: To implement pagination, you can keep track of the current page number
and increment it each time the user reaches the end of the table view. You can
use this page number to construct the URL to fetch the next page of articles
from the API.

Here's an example implementation:

```swift

class NewsViewController: UIViewController {

    var articles: [Article] = []
    var currentPage = 1

    // ...

    func fetchArticles() {
        let urlString = "https://api.example.com/articles?page=\(currentPage)"
        guard let url = URL(string: urlString) else { return }

        URLSession.shared.dataTask(with: url) { [weak self] (data, response, error) in
            guard let data = data else { return }

            let decoder = JSONDecoder()
            decoder.keyDecodingStrategy = .convertFromSnakeCase

            do {
                let result = try decoder.decode(ArticleList.self, from: data)
                self?.articles.append(contentsOf: result.articles)
                self?.tableView.reloadData()
            } catch {
                print(error)
            }
        }.resume()
    }

    func loadNextPage() {
        currentPage += 1
        fetchArticles()
    }

    // ...
}

extension NewsViewController: UITableViewDataSourcePrefetching {
    func tableView(_ tableView: UITableView, prefetchRowsAt indexPaths: [IndexPath]) {
        if let lastIndexPath = indexPaths.last, lastIndexPath.row >= articles.count - 1 {
            loadNextPage()
        }
    }
}
```

This implementation adds a **`currentPage`** property to keep track of the
current page number, and constructs the URL to fetch the next page of articles
based on this value. It also adds a **`loadNextPage()`** method to increment the
page number and fetch the next page of articles. Finally, it adopts the
**`UITableViewDataSourcePrefetching`** protocol to detect when the user scrolls
to the end of the table view, and calls **`loadNextPage()`** to load the next
page of articles.

The key difference between this task and the previous Junior 1 tasks is the
addition of pagination. This requires more complex logic to keep track of the
current page and load the next page of articles as the user scrolls. It also
demonstrates a deeper understanding of asynchronous data loading and networking
concepts.

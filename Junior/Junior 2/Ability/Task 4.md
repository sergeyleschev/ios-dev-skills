# Task 4

Task: Implement a news feed feature for the app that shows the latest news
articles from the API. The news feed should display the title, thumbnail image,
and a brief summary of each article. The user should be able to pull to refresh
the feed to see the latest news.

Solution: To implement this task, we can start by creating a
**`NewsFeedViewController`** that displays a table view of news articles. We can
use **`URLSession`** and **`JSONDecoder`** to fetch and parse the JSON response
from the API. Once we have the news articles, we can display them in the table
view by creating a custom **`NewsTableViewCell`** that displays the title,
thumbnail image, and summary of each article.

Here's an example implementation:

```swift
class NewsFeedViewController: UIViewController {

    private let tableView = UITableView()

    private var newsArticles: [NewsArticle] = []

    override func viewDidLoad() {
        super.viewDidLoad()

        // Setup table view
        tableView.dataSource = self
        tableView.register(NewsTableViewCell.self, forCellReuseIdentifier: "NewsCell")
        view.addSubview(tableView)

        // Fetch news articles
        fetchNewsArticles()
    }

    override func viewDidLayoutSubviews() {
        super.viewDidLayoutSubviews()

        tableView.frame = view.bounds
    }

    private func fetchNewsArticles() {
        let url = URL(string: "https://example.com/api/news")!
        URLSession.shared.dataTask(with: url) { data, response, error in
            guard let data = data else { return }
            do {
                let decoder = JSONDecoder()
                let articles = try decoder.decode([NewsArticle].self, from: data)
                DispatchQueue.main.async {
                    self.newsArticles = articles
                    self.tableView.reloadData()
                }
            } catch {
                print("Error decoding news articles: \(error.localizedDescription)")
            }
        }.resume()
    }
}

extension NewsFeedViewController: UITableViewDataSource {

    func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        return newsArticles.count
    }

    func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
        let cell = tableView.dequeueReusableCell(withIdentifier: "NewsCell", for: indexPath) as! NewsTableViewCell
        let article = newsArticles[indexPath.row]
        cell.titleLabel.text = article.title
        cell.summaryLabel.text = article.summary
        if let thumbnailURL = article.thumbnailURL {
            cell.thumbnailImageView.load(from: thumbnailURL)
        }
        return cell
    }
}

```

Differences from Junior 1 level:

-   This task involves fetching data from a remote API, which requires knowledge
    of **`URLSession`** and **`JSONDecoder`**.
-   The table view displays more information about each news article, including
    a thumbnail image and summary.
-   The app supports pull-to-refresh, which requires knowledge of
    UIRefreshControl.
-   The app architecture is more complex, with a custom **`NewsTableViewCell`**
    and a separate **`fetchNewsArticles()`** method.

# Task 4

Task: Add a detail view controller that displays the full article content when a
table view cell is tapped.

Solution:

```swift
func tableView(_ tableView: UITableView, didSelectRowAt indexPath: IndexPath) {
    let article = isSearching ? filteredNewsArticles[indexPath.row] : newsArticles[indexPath.row]
    let detailVC = NewsArticleDetailViewController(article: article)
    navigationController?.pushViewController(detailVC, animated: true)
}

class NewsArticleDetailViewController: UIViewController {
    let article: NewsArticle

    init(article: NewsArticle) {
        self.article = article
        super.init(nibName: nil, bundle: nil)
    }

    required init?(coder: NSCoder) {
        fatalError("init(coder:) has not been implemented")
    }

    override func viewDidLoad() {
        super.viewDidLoad()
        // configure the detail view UI using the article property
    }
}

```

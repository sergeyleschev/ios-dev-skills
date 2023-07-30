# Task 1

Task: Implement a UITableView that displays a list of news articles retrieved
from a JSON API. Each cell should display the article's title, author, and
publication date.

Solution:

```swift
// Assuming data retrieved from API is stored in an array of NewsArticle objects
class NewsTableViewController: UITableViewController {
    var articles: [NewsArticle] = []

    override func viewDidLoad() {
        super.viewDidLoad()

        tableView.register(UITableViewCell.self, forCellReuseIdentifier: "cell")
        tableView.tableFooterView = UIView() // Hide empty cells at bottom of table
        tableView.dataSource = self
        tableView.delegate = self

        retrieveDataFromAPI()
    }

    func retrieveDataFromAPI() {
        // Code to retrieve data from API and populate `articles` array goes here
    }

    override func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        return articles.count
    }

    override func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
        let cell = tableView.dequeueReusableCell(withIdentifier: "cell", for: indexPath)

        let article = articles[indexPath.row]
        cell.textLabel?.text = article.title
        cell.detailTextLabel?.text = "\(article.author) - \(article.publicationDate)"

        return cell
    }
}

```

Difference from Junior 1:

-   Retrieving data from a JSON API instead of using static data.
-   Implementing a UITableView instead of just displaying a single view.

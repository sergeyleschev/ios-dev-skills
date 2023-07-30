# Task 5

Task: Create a view controller that displays a list of articles retrieved from
an API endpoint. Each article should display its title, author, and date
published. When a user taps on an article, the app should navigate to a detail
view controller that displays the full article text.

Requirements:

-   Use URLSession to retrieve the JSON data from the API endpoint
-   Use Codable to parse the JSON data into Swift models
-   Display the list of articles in a table view
-   When a user taps on an article, pass the selected article to the detail view
    controller using a segue

Solution:

```swift
import UIKit

class ArticleListViewController: UIViewController {

    @IBOutlet weak var tableView: UITableView!

    var articles: [Article] = []

    override func viewDidLoad() {
        super.viewDidLoad()

        tableView.delegate = self
        tableView.dataSource = self

        fetchData()
    }

    func fetchData() {
        guard let url = URL(string: "https://api.example.com/articles") else { return }

        let task = URLSession.shared.dataTask(with: url) { (data, response, error) in
            guard let data = data else { return }

            do {
                let decoder = JSONDecoder()
                self.articles = try decoder.decode([Article].self, from: data)

                DispatchQueue.main.async {
                    self.tableView.reloadData()
                }
            } catch let error {
                print("Error decoding JSON: \(error.localizedDescription)")
            }
        }

        task.resume()
    }

    override func prepare(for segue: UIStoryboardSegue, sender: Any?) {
        if segue.identifier == "showArticleDetail", let destination = segue.destination as? ArticleDetailViewController, let selectedIndexPath = tableView.indexPathForSelectedRow {
            destination.article = articles[selectedIndexPath.row]
        }
    }

}

extension ArticleListViewController: UITableViewDelegate, UITableViewDataSource {

    func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        return articles.count
    }

    func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
        let cell = tableView.dequeueReusableCell(withIdentifier: "ArticleCell", for: indexPath) as! ArticleCell

        let article = articles[indexPath.row]
        cell.titleLabel.text = article.title
        cell.authorLabel.text = "By \(article.author)"
        cell.dateLabel.text = article.datePublished

        return cell
    }

}

class ArticleDetailViewController: UIViewController {

    @IBOutlet weak var titleLabel: UILabel!
    @IBOutlet weak var textView: UITextView!

    var article: Article?

    override func viewDidLoad() {
        super.viewDidLoad()

        if let article = article {
            titleLabel.text = article.title
            textView.text = article.text
        }
    }

}

struct Article: Codable {
    let title: String
    let author: String
    let datePublished: String
    let text: String

    enum CodingKeys: String, CodingKey {
        case title
        case author
        case datePublished = "date_published"
        case text
    }
}

class ArticleCell: UITableViewCell {

    @IBOutlet weak var titleLabel: UILabel!
    @IBOutlet weak var authorLabel: UILabel!
    @IBOutlet weak var dateLabel: UILabel!

}

```

Differences from Junior 1 level:

-   The task requires the use of more advanced topics such as URLSession,
    Codable, and table view delegates and data sources.
-   The app must fetch data from an API endpoint, rather than using hardcoded
    data.
-   The app must display the retrieved data in a table view, rather than a
    simple view.
-   The app must pass data between view controllers using segues, rather than
    simply displaying data on a single view controller.

# Task 5

Task: Implement a function that fetches news articles from a given API and
displays them in a table view. The table view should show the article's title,
author, and date. When a user taps on a cell, it should navigate to a new view
controller that displays the article's content in a web view. Use the following
API endpoint: **https://jsonplaceholder.typicode.com/posts**

Solution:

First, we need to define a model for the news article:

```swift
struct NewsArticle: Codable {
    let title: String
    let author: String
    let date: String
    let content: String

    enum CodingKeys: String, CodingKey {
        case title = "title"
        case author = "userId"
        case date = "id"
        case content = "body"
    }
}

```

Next, we need to create a function to fetch the news articles from the API:

```swift
func fetchNewsArticles(completion: @escaping ([NewsArticle]?, Error?) -> Void) {
    guard let url = URL(string: "https://jsonplaceholder.typicode.com/posts") else {
        return
    }

    URLSession.shared.dataTask(with: url) { data, response, error in
        guard let data = data else {
            completion(nil, error)
            return
        }

        do {
            let articles = try JSONDecoder().decode([NewsArticle].self, from: data)
            completion(articles, nil)
        } catch {
            completion(nil, error)
        }
    }.resume()
}

```

Then, we need to create a table view to display the news articles:

```swift
class NewsTableViewController: UITableViewController {
    var articles: [NewsArticle] = []

    override func viewDidLoad() {
        super.viewDidLoad()

        fetchNewsArticles { articles, error in
            if let articles = articles {
                self.articles = articles

                DispatchQueue.main.async {
                    self.tableView.reloadData()
                }
            } else if let error = error {
                print(error.localizedDescription)
            }
        }
    }

    override func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        return articles.count
    }

    override func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
        let cell = tableView.dequeueReusableCell(withIdentifier: "NewsCell", for: indexPath)
        let article = articles[indexPath.row]

        cell.textLabel?.text = article.title
        cell.detailTextLabel?.text = "\(article.author) - \(article.date)"

        return cell
    }

    override func tableView(_ tableView: UITableView, didSelectRowAt indexPath: IndexPath) {
        let article = articles[indexPath.row]
        let webViewController = WebViewController(url: URL(string: "https://google.com")!) // Replace with article URL
        navigationController?.pushViewController(webViewController, animated: true)
    }
}

```

Finally, we need to create a view controller to display the article content in a
web view:

```swift
class WebViewController: UIViewController {
    var url: URL

    init(url: URL) {
        self.url = url

        super.init(nibName: nil, bundle: nil)
    }

    required init?(coder: NSCoder) {
        fatalError("init(coder:) has not been implemented")
    }

    override func viewDidLoad() {
        super.viewDidLoad()

        let webView = WKWebView(frame: view.frame)
        view.addSubview(webView)

        webView.load(URLRequest(url: url))
    }
}

```

Differences from Junior 1 level:

-   The task requires fetching data from an external API, which requires
    knowledge of networking and working with JSON data.
-   The task requires displaying data in a table view, which requires knowledge

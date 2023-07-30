# Task 1

Task: Retrieve a list of news articles from a JSON API and display them in a
table view.

Solution:

```swift
func fetchNewsArticles() {
    guard let url = URL(string: "https://example.com/news") else {
        return
    }

    URLSession.shared.dataTask(with: url) { data, response, error in
        if let error = error {
            print("Error fetching news articles: \(error.localizedDescription)")
            return
        }

        guard let data = data else {
            print("No data returned from news API.")
            return
        }

        do {
            let decoder = JSONDecoder()
            let articles = try decoder.decode([NewsArticle].self, from: data)
            DispatchQueue.main.async {
                self.newsArticles = articles
                self.tableView.reloadData()
            }
        } catch let error {
            print("Error decoding news articles: \(error.localizedDescription)")
        }
    }.resume()
}

```

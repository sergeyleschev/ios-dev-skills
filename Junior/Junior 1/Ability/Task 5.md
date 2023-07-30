# Task 5

Task: Implement error handling for network and decoding errors.

Solution:

```swift
import Foundation

enum NewsAppError: Error {
    case networkError(Error)
    case decodingError(Error)
}

func fetchNewsArticles(completion: @escaping (Result<[NewsArticle], NewsAppError>) -> Void) {
    guard let url = URL(string: "https://example.com/news") else {
        // Handle invalid URL error
        completion(.failure(.networkError(NSError(domain: "Invalid URL", code: 0, userInfo: nil))))
        return
    }

    let session = URLSession.shared
    let task = session.dataTask(with: url) { data, response, error in
        if let error = error {
            // Handle network error
            completion(.failure(.networkError(error)))
            return
        }

        guard let httpResponse = response as? HTTPURLResponse else {
            // Handle invalid HTTP response
            completion(.failure(.networkError(NSError(domain: "Invalid HTTP response", code: 0, userInfo: nil))))
            return
        }

        if httpResponse.statusCode == 200 {
            // Successful response
            do {
                // Decode the JSON data into NewsArticle objects
                let decoder = JSONDecoder()
                let articles = try decoder.decode([NewsArticle].self, from: data!)
                completion(.success(articles))
            } catch let decodingError {
                // Handle decoding error
                completion(.failure(.decodingError(decodingError)))
            }
        } else {
            // Handle HTTP error status code
            completion(.failure(.networkError(NSError(domain: "HTTP Error: \(httpResponse.statusCode)", code: httpResponse.statusCode, userInfo: nil))))
        }
    }
    task.resume()
}

// Example NewsArticle struct, update it according to your actual data structure
struct NewsArticle: Codable {
    let title: String
    let content: String
    // Add other properties as needed
}

// Usage example
fetchNewsArticles { result in
    switch result {
    case .success(let articles):
        // Handle retrieved articles
        print("Fetched \(articles.count) news articles.")
    case .failure(let error):
        // Handle error
        print("Error: \(error)")
    }
}


```

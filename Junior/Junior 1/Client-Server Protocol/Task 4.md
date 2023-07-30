# Task 4

Task: Create an iOS app that allows users to search for movies using the OMDB
API and displays the results in a UICollectionView.

Solution:

1. Create a new Xcode project and select "Single View App" template.
2. Open ViewController.swift and add the following code:

```swift
import UIKit

class ViewController: UIViewController, UICollectionViewDelegate, UICollectionViewDataSource, UICollectionViewDelegateFlowLayout, UISearchBarDelegate {

    @IBOutlet weak var collectionView: UICollectionView!
    @IBOutlet weak var searchBar: UISearchBar!

    var movies: [Movie] = []

    override func viewDidLoad() {
        super.viewDidLoad()

        collectionView.delegate = self
        collectionView.dataSource = self

        searchBar.delegate = self
    }

    func searchBarSearchButtonClicked(_ searchBar: UISearchBar) {
        guard let searchText = searchBar.text?.trimmingCharacters(in: .whitespacesAndNewlines),
            !searchText.isEmpty else {
            return
        }

        let url = "http://www.omdbapi.com/?apikey=<Your API key>&s=\(searchText)"

        guard let encodedUrl = url.addingPercentEncoding(withAllowedCharacters: .urlQueryAllowed),
            let finalUrl = URL(string: encodedUrl) else {
            return
        }

        URLSession.shared.dataTask(with: finalUrl) { data, response, error in
            guard let data = data else { return }

            do {
                let searchResult = try JSONDecoder().decode(SearchResult.self, from: data)
                self.movies = searchResult.Search
                DispatchQueue.main.async {
                    self.collectionView.reloadData()
                }
            } catch {
                print(error.localizedDescription)
            }
        }.resume()
    }

    func collectionView(_ collectionView: UICollectionView, numberOfItemsInSection section: Int) -> Int {
        return movies.count
    }

    func collectionView(_ collectionView: UICollectionView, cellForItemAt indexPath: IndexPath) -> UICollectionViewCell {
        let cell = collectionView.dequeueReusableCell(withReuseIdentifier: "cell", for: indexPath) as! MovieCollectionViewCell

        let movie = movies[indexPath.row]
        cell.titleLabel.text = movie.Title

        if let posterUrl = movie.Poster, let url = URL(string: posterUrl) {
            URLSession.shared.dataTask(with: url) { data, response, error in
                guard let data = data, let image = UIImage(data: data) else { return }
                DispatchQueue.main.async {
                    cell.posterImageView.image = image
                }
            }.resume()
        }

        return cell
    }

    func collectionView(_ collectionView: UICollectionView, layout collectionViewLayout: UICollectionViewLayout, sizeForItemAt indexPath: IndexPath) -> CGSize {
        let width = (view.frame.width - 30) / 2
        let height = width * 1.5
        return CGSize(width: width, height: height)
    }

}

struct SearchResult: Codable {
    let Search: [Movie]
    let totalResults: String
    let Response: String
}

struct Movie: Codable {
    let Title: String
    let Year: String
    let imdbID: String
    let `Type`: String
    let Poster: String?
}

```

3. Open Main.storyboard and add a UICollectionView to the ViewController. Set
   the UICollectionView's dataSource, delegate and cell prototype to the
   ViewController.
4. Create a UICollectionViewCell with a reuseIdentifier of "cell". Add a
   UIImageView for the movie poster and a UILabel for the movie title.
5. Add a UISearchBar to the top of the ViewController.
6. Get an API key from OMDB API (**http://www.omdbapi.com/**).
7. Replace <Your API key> in the url constant in the
   searchBarSearchButtonClicked method with the API key you obtained.
8. Run the app and search for movies using the

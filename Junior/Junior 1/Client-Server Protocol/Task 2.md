# Task 2

Task: You need to create an iOS app that retrieves JSON data from an API
endpoint and displays the data in a UICollectionView. The API endpoint is:
**https://jsonplaceholder.typicode.com/photos**

Solution:

1. Create a new Xcode project and select "Single View App" template.
2. Open ViewController.swift and add the following code:

```swift
import UIKit

class ViewController: UIViewController, UICollectionViewDelegate, UICollectionViewDataSource, UICollectionViewDelegateFlowLayout {

    @IBOutlet weak var collectionView: UICollectionView!

    var photos: [Photo] = []

    override func viewDidLoad() {
        super.viewDidLoad()

        collectionView.delegate = self
        collectionView.dataSource = self

        let layout = UICollectionViewFlowLayout()
        layout.minimumInteritemSpacing = 10
        layout.minimumLineSpacing = 10
        collectionView.collectionViewLayout = layout

        getData()
    }

    func getData() {
        guard let url = URL(string: "https://jsonplaceholder.typicode.com/photos") else { return }

        URLSession.shared.dataTask(with: url) { data, response, error in
            guard let data = data else { return }

            do {
                self.photos = try JSONDecoder().decode([Photo].self, from: data)
                DispatchQueue.main.async {
                    self.collectionView.reloadData()
                }
            } catch {
                print(error.localizedDescription)
            }
        }.resume()
    }

    func collectionView(_ collectionView: UICollectionView, numberOfItemsInSection section: Int) -> Int {
        return photos.count
    }

    func collectionView(_ collectionView: UICollectionView, cellForItemAt indexPath: IndexPath) -> UICollectionViewCell {
        let cell = collectionView.dequeueReusableCell(withReuseIdentifier: "cell", for: indexPath) as! PhotoCell

        let photo = photos[indexPath.item]
        cell.imageView.image = UIImage(named: "placeholder")

        DispatchQueue.global().async {
            guard let url = URL(string: photo.url) else { return }
            guard let data = try? Data(contentsOf: url) else { return }

            DispatchQueue.main.async {
                if let currentIndexPath = collectionView.indexPath(for: cell), currentIndexPath == indexPath {
                    cell.imageView.image = UIImage(data: data)
                }
            }
        }

        return cell
    }

    func collectionView(_ collectionView: UICollectionView, layout collectionViewLayout: UICollectionViewLayout, sizeForItemAt indexPath: IndexPath) -> CGSize {
        let width = (collectionView.frame.size.width - 30) / 2
        let height = width * 1.5
        return CGSize(width: width, height: height)
    }

}

class PhotoCell: UICollectionViewCell {

    @IBOutlet weak var imageView: UIImageView!

    override func prepareForReuse() {
        imageView.image = nil
    }

}

```

3. Create a new file called "Photo.swift" and add the following code:

```swift
import Foundation

struct Photo: Codable {
    let albumId: Int
    let id: Int
    let title: String
    let url: String
    let thumbnailUrl: String
}

```

4. Open Main.storyboard and add a UICollectionView to the ViewController. Set
   the UICollectionView's dataSource, delegate and cell prototype to the
   ViewController.
5. Create a UICollectionViewCell with a reuseIdentifier of "cell". Add a
   UIImageView to the cell and set its tag to 1.
6. Run the app and the JSON data should be displayed in the UICollectionView.

Note: This code uses URLSession to make a network request and decode the JSON
response using Codable. It also uses GCD to load the images asynchronously and
update the UI on the main thread. The cell's prepareForReuse method ensures that
old images are cleared before new ones are loaded.

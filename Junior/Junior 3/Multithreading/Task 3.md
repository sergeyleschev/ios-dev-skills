# Task 3

Task: Create an iOS app that uses GCD to download an image from a URL and
display it in an UIImageView.

Solution:

Create a ViewController with an UIImageView:

```swift
class ViewController: UIViewController {
    @IBOutlet weak var imageView: UIImageView!

    override func viewDidLoad() {
        super.viewDidLoad()
        self.downloadImage()
    }

    func downloadImage() {
        guard let url = URL(string: "https://example.com/image.png") else { return }
        DispatchQueue.global(qos: .userInitiated).async {
            do {
                let imageData = try Data(contentsOf: url)
                let image = UIImage(data: imageData)
                DispatchQueue.main.async {
                    self.imageView.image = image
                }
            } catch {
                print(error.localizedDescription)
            }
        }
    }
}
```

Differences from Junior 2 level:

-   The use of GCD to perform a time-consuming task (downloading an image) in
    the background.
-   The use of different quality of service (QoS) levels to prioritize tasks.
-   The use of try-catch to handle errors when loading data from a URL.
-   The use of DispatchQueue.main.async to update the UI on the main thread.

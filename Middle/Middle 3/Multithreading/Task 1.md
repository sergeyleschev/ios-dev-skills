# Task 1

Task: Write a function that downloads an image from a remote URL using
URLSession and displays it on a UIImageView on the main thread. However, the
image download should happen on a background thread and should be cancelled
after 5 seconds if it takes too long. If the download is cancelled, the
UIImageView should display a placeholder image instead. Use GCD to perform the
background task and ensure thread safety.

Solution:

```swift
func downloadImage(from url: URL, imageView: UIImageView) {
    let session = URLSession.shared

    // Create a background queue
    let backgroundQueue = DispatchQueue.global(qos: .background)

    // Download image on background thread
    var task: URLSessionDataTask?
    backgroundQueue.async {
        task = session.dataTask(with: url) { (data, response, error) in
            guard error == nil, let data = data, let image = UIImage(data: data) else {
                // Display placeholder image on main thread if download failed
                DispatchQueue.main.async {
                    imageView.image = UIImage(named: "placeholder")
                }
                return
            }

            // Display downloaded image on main thread
            DispatchQueue.main.async {
                imageView.image = image
            }
        }

        // Start the download task and cancel it after 5 seconds if it takes too long
        task?.resume()
        backgroundQueue.asyncAfter(deadline: .now() + 5) {
            if let task = task, task.state == .running {
                task.cancel()
                DispatchQueue.main.async {
                    imageView.image = UIImage(named: "placeholder")
                }
            }
        }
    }
}
```

Differences from the previous level (Middle 2):

-   The solution involves using GCD to perform the background task instead of
    just creating a background thread
-   The solution includes cancelling the download task after 5 seconds if it
    takes too long
-   The solution handles thread safety by ensuring that UI updates happen on the
    main thread.

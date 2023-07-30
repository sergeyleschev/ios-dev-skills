# Task 3

Task: You are given an array of image URLs. Write a function that downloads
these images asynchronously and displays them in a UICollectionView. Each image
should be displayed in a UICollectionViewCell. The image download should happen
on a background thread and should be cancelled after 5 seconds if it takes too
long. If the download is cancelled, the UICollectionViewCell should display a
placeholder image instead. Use GCD to perform the background task and ensure
thread safety.

Solution:

```swift
func downloadImages(_ urls: [URL], completion: @escaping ([UIImage]) -> Void) {
    let session = URLSession.shared

    // Create a background queue
    let backgroundQueue = DispatchQueue.global(qos: .background)

    var images: [UIImage] = []
    var cancelled = false
    var remainingCount = urls.count

    for url in urls {
        // Download image on background thread
        backgroundQueue.async {
            let task = session.dataTask(with: url) { (data, response, error) in
                guard error == nil, let data = data, let image = UIImage(data: data) else {
                    // Display placeholder image on main thread if download failed
                    DispatchQueue.main.async {
                        images.append(UIImage(named: "placeholder")!)
                        remainingCount -= 1
                        if remainingCount == 0 {
                            completion(images)
                        }
                    }
                    return
                }

                // Display downloaded image on main thread
                DispatchQueue.main.async {
                    images.append(image)
                    remainingCount -= 1
                    if remainingCount == 0 {
                        completion(images)
                    }
                }
            }

            // Start the download task and cancel it after 5 seconds if it takes too long
            task.resume()
            backgroundQueue.asyncAfter(deadline: .now() + 5) {
                if !cancelled && task.state == .running {
                    task.cancel()
                    cancelled = true
                    DispatchQueue.main.async {
                        images.append(UIImage(named: "placeholder")!)
                        remainingCount -= 1
                        if remainingCount == 0 {
                            completion(images)
                        }
                    }
                }
            }
        }
    }
}
```

Differences from the previous level (Middle 2):

-   The solution involves downloading multiple images asynchronously and
    displaying them in a UICollectionView, whereas the previous tasks only
    involved downloading a single image or calculating a sum
-   The solution uses a loop to iterate over multiple URLs and download the
    images asynchronously, which requires more complex handling of the
    completion block and cancellation of the download task
-   The solution uses a counter to keep track of the remaining number of images
    to download and displays the images in a UICollectionView, which requires
    more advanced knowledge of UIKit.

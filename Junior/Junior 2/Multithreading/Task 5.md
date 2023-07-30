# Task 5

Task: Implement a function that downloads an image from a remote server using
URLSession, and displays it in an image view. The function should be
asynchronous and be called from the main thread.

Solution:

```swift
func downloadAndDisplayImage(from url: URL, in imageView: UIImageView) {
    let task = URLSession.shared.dataTask(with: url) { data, response, error in
        guard let data = data, error == nil else {
            print("Error: \(error!.localizedDescription)")
            return
        }

        DispatchQueue.main.async {
            imageView.image = UIImage(data: data)
        }
    }
    task.resume()
}
```

Differences from Junior Level 1:

-   The task involves downloading an image from a remote server using
    URLSession, which requires a slightly more advanced understanding of
    networking.
-   The solution includes using a completion handler to asynchronously handle
    the network response, which shows an understanding of asynchronous
    programming.
-   The solution uses **`DispatchQueue.main.async`** to update the UI on the
    main thread, which demonstrates an understanding of multithreading and
    avoiding UI updates on a background thread.

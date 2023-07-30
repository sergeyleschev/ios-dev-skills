# Task 3

Task: Write a function that downloads an image from a remote URL and displays it
in a UIImageView. Ensure that the function does not cause a memory leak.

Solution:

```swift
func displayImage(from url: URL, in imageView: UIImageView) {
    URLSession.shared.dataTask(with: url) { data, response, error in
        if let error = error {
            print("Error: \(error.localizedDescription)")
            return
        }

        guard let data = data, let image = UIImage(data: data) else {
            print("Invalid image data")
            return
        }

        DispatchQueue.main.async {
            imageView.image = image
        }
    }.resume()
}
```

To prevent a memory leak, we are using a data task with a completion closure
instead of a synchronous request. The closure is executed asynchronously on a
background thread, and the data task is released when it finishes. We are also
ensuring that the UIImageView is updated on the main thread.

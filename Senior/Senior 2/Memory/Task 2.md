# Task 2

Task: Write a function that downloads an image from a URL and displays it in an
image view. Ensure that the function does not cause a memory leak.

Solution:

```swift
func loadImage(from urlString: String, into imageView: UIImageView) {
    guard let url = URL(string: urlString) else {
        return
    }

    DispatchQueue.global(qos: .userInitiated).async {
        guard let imageData = try? Data(contentsOf: url) else {
            return
        }

        let image = UIImage(data: imageData)

        DispatchQueue.main.async {
            imageView.image = image
        }
    }
}
```

In this solution, we use a **`guard`** statement to ensure that the URL is
valid. We then use a global **`DispatchQueue`** to download the image data
asynchronously. Once the data has been downloaded and converted to a
**`UIImage`**, we switch to the main thread to set the image on the
**`UIImageView`**.

To ensure that this function does not cause a memory leak, we do not retain any
strong references to the **`UIImageView`** or the **`UIImage`** object. Once the
function has completed and the image has been displayed, the **`UIImage`**
object will be released from memory when it is no longer needed.

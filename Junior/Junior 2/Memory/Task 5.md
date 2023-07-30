# Task 5

## **Task**

Your team is working on a new feature for your app, which requires you to load
and display a large image. You have written the following code to load the image
and display it in a UIImageView:

```swift
let imageView = UIImageView()

func loadImage() {
    guard let url = URL(string: "https://example.com/large_image.png") else { return }
    DispatchQueue.global(qos: .userInitiated).async {
        guard let data = try? Data(contentsOf: url) else { return }
        let image = UIImage(data: data)
        DispatchQueue.main.async {
            self.imageView.image = image
        }
    }
}
```

After testing your feature, you noticed that the memory usage of your app
increases significantly every time you load the image, and it's not being
released even when the view controller is dismissed. How would you fix this
memory leak issue?

## **Solution**

The memory leak issue in the above code is due to the strong reference cycle
created between the closure and the view controller. To fix this issue, we can
use an unowned reference to self in the closure or capture a weak reference to
self instead. Here's an updated code with the weak reference capture:

```swift
swiftCopy code
let imageView = UIImageView()

func loadImage() {
    guard let url = URL(string: "https://example.com/large_image.png") else { return }
    DispatchQueue.global(qos: .userInitiated).async { [weak self] in
        guard let data = try? Data(contentsOf: url) else { return }
        let image = UIImage(data: data)
        DispatchQueue.main.async {
            self?.imageView.image = image
        }
    }
}
```

By capturing a weak reference to self, we avoid the strong reference cycle and
allow the view controller to be released from memory once it's dismissed. This
will prevent the memory leak issue and ensure that the app runs smoothly even
when loading large images.

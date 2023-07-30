# Task 3

Task: Implement a function that takes an array of URLs and downloads the images
from those URLs in parallel using Grand Central Dispatch. Once all the images
are downloaded, display them in a collection view.

Solution:

```swift
func downloadImagesFromURLs(_ urls: [URL], completion: @escaping ([UIImage]) -> Void) {
    var images = [UIImage]()
    let dispatchGroup = DispatchGroup()
    let dispatchQueue = DispatchQueue.global(qos: .userInitiated)

    for url in urls {
        dispatchGroup.enter()
        dispatchQueue.async {
            if let data = try? Data(contentsOf: url), let image = UIImage(data: data) {
                images.append(image)
            }
            dispatchGroup.leave()
        }
    }

    dispatchGroup.notify(queue: .main) {
        completion(images)
    }
}

// Usage
downloadImagesFromURLs(urls) { images in
    self.images = images
    self.collectionView.reloadData()
}
```

Differences from Junior 1 level:

-   The task involves parallel downloading of images using Grand Central
    Dispatch, which requires knowledge of concurrency and multithreading.
-   The use of **`DispatchGroup`** and **`DispatchQueue`** shows an
    understanding of managing and synchronizing concurrent tasks.
-   The completion handler with a returned array of **`UIImage`**s shows
    knowledge of asynchronous programming and callback functions.

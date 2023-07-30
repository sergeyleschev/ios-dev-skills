# Task 5

Task: Implement a thread-safe cache that stores images downloaded from the
network. The cache should support storing and retrieving images by their URLs,
and it should limit the number of stored images to a fixed maximum. If a request
is made for an image that is not in the cache, it should be downloaded from the
network and added to the cache. Use the **`NSCache`** class for storing the
images and implement thread synchronization to ensure that the cache is accessed
safely by multiple threads.

Solution:

```swift
class ImageCache {
    private let cache = NSCache<NSString, UIImage>()
    private let lock = NSLock()
    private let maxCacheSize: Int

    init(maxCacheSize: Int) {
        self.maxCacheSize = maxCacheSize
        cache.countLimit = maxCacheSize
    }

    func getImage(for url: URL, completion: @escaping (UIImage?) -> Void) {
        lock.lock()
        defer { lock.unlock() }

        if let image = cache.object(forKey: url.absoluteString as NSString) {
            completion(image)
            return
        }

        downloadImage(from: url) { [weak self] image in
            guard let self = self else { return }
            if let image = image {
                self.cache.setObject(image, forKey: url.absoluteString as NSString)
                completion(image)
            } else {
                completion(nil)
            }
        }
    }

    private func downloadImage(from url: URL, completion: @escaping (UIImage?) -> Void) {
        URLSession.shared.dataTask(with: url) { data, response, error in
            guard let data = data, let image = UIImage(data: data) else {
                completion(nil)
                return
            }
            completion(image)
        }.resume()
    }
}
```

Differences from the previous task:

-   The previous task focused on using GCD for multithreading, while this task
    uses **`NSLock`** for thread synchronization.
-   This task also involves using **`NSCache`** for caching images, while the
    previous task used a simple array for storing data.
-   The problem being solved in this task is also more complex, as it involves
    not only thread synchronization but also downloading images from the network
    and limiting the cache size.

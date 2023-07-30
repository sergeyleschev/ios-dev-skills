# Task 3

Task: Implement a custom image caching mechanism to improve performance and
avoid memory leaks in a photo gallery app.

Solution:

1. Create a singleton class **`ImageCacheManager`** that will handle caching and
   fetching of images.
2. Use **`NSCache`** to store images in memory with their URLs as keys.
3. Implement a method
   **`getImage(from url: URL, completion: @escaping (UIImage?) -> Void)`** in
   **`ImageCacheManager`** that checks if the image exists in the cache. If it
   does, return it. If not, download the image using **`URLSession`** and store
   it in the cache before returning it.
4. Use the **`completion`** closure to return the image to the caller.
5. In the photo gallery view controller, use the **`ImageCacheManager`** to
   fetch images instead of loading them synchronously.
6. Make sure to remove images from the cache when they are no longer needed to
   prevent memory leaks. Use the **`NSCacheDelegate`** method
   **`cache(_ cache: NSCache<AnyObject, AnyObject>, willEvictObject obj: Any)`**
   to track when images are removed from the cache.

Differences that indicate the development of the developer to the level of
Middle 1 from the level of Junior 3:

1. The task requires the implementation of a custom caching mechanism instead of
   simply using existing frameworks like **`SDWebImage`**. This indicates a
   deeper understanding of memory management and performance optimization.
2. The use of a singleton pattern for the **`ImageCacheManager`** demonstrates
   knowledge of design patterns and architectural concepts.
3. The use of the **`NSCacheDelegate`** method to track image evictions shows a
   more advanced understanding of the **`NSCache`** framework.

# Task 3

Task: You are given an iOS app that displays a list of images in a
UICollectionView. Each image is loaded asynchronously from a URL using
URLSession.shared.dataTask(). However, you have noticed that after scrolling
through the list multiple times, the app starts to slow down and eventually
crashes due to a memory issue. Your task is to identify and fix the memory leak
causing the issue.

Solution:

Step 1: Identify the cause of the memory leak The first step is to identify what
is causing the memory leak. We can use Xcode's memory graph debugger to help us
with this. Open the project in Xcode, run it on a device or simulator, and then
open the Debug Navigator. Click on the "Memory" tab to show the memory graph.
Click on the "Record" button to start recording memory allocations.

Now, scroll through the list multiple times and notice that the memory usage
keeps increasing. Stop recording and take a look at the memory graph. You should
see that there are many instances of the image data that are not being released
from memory. This is a clear indication that we have a memory leak.

Step 2: Fix the memory leak The most common cause of memory leaks in iOS apps is
retaining objects in a closure or a reference cycle. In our case, we can see
that the image data is being retained in memory because of the
URLSession.shared.dataTask() closure.

To fix this, we need to make sure that we are releasing the image data when we
don't need it anymore. One way to do this is to use a cache to store the image
data that we have already loaded. Modify the code that loads the image as
follows:

```swift
func loadImage(from url: URL, completion: @escaping (UIImage?) -> Void) {
    if let cachedImage = imageCache.object(forKey: url.absoluteString as NSString) {
        completion(cachedImage)
        return
    }

    let task = URLSession.shared.dataTask(with: url) { [weak self] (data, response, error) in
        guard let self = self else { return }

        guard error == nil,
            let data = data,
            let image = UIImage(data: data) else {
                completion(nil)
                return
        }

        self.imageCache.setObject(image, forKey: url.absoluteString as NSString)
        completion(image)
    }
    task.resume()
}
```

We have added an imageCache property, which is an instance of NSCache. We check
if the image is already in the cache, and if it is, we return it directly. If
not, we load it asynchronously using URLSession.shared.dataTask(), and store it
in the cache when it's loaded.

Additionally, we have used [weak self] in the closure to prevent a retain cycle.

Step 3: Test the app Run the app again and repeat the same steps. Notice that
the memory usage no longer keeps increasing, and the app does not crash due to a
memory issue. The problem has been fixed!

Note: This is just one way to fix a memory leak in this particular scenario.
There can be many other causes of memory leaks in iOS apps, and it's important
to understand how to identify and fix them. Additionally, testing the app
thoroughly after making any changes is crucial to ensure that the problem has
been resolved.

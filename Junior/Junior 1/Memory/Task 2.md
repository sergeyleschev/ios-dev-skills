# Task 2

Task: You are given an iOS app that uses a UITableViewController to display a
list of items. Each item is represented by a custom UITableViewCell that
displays an image and some text. However, you have noticed that after scrolling
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
see that there are many instances of the custom UITableViewCell that are not
being released from memory. This is a clear indication that we have a memory
leak.

Step 2: Fix the memory leak The most common cause of memory leaks in iOS apps is
retaining objects in a closure or a reference cycle. In our case, we can see
that the custom UITableViewCell is being retained in memory because of the image
property.

To fix this, we need to make sure that we are only loading the image when we
need it, and releasing it when we don't. One way to do this is to use a cache to
store the images that we have already loaded. Modify the custom UITableViewCell
code as follows:

```swift
class CustomTableViewCell: UITableViewCell {
    @IBOutlet weak var customImageView: UIImageView!
    @IBOutlet weak var customLabel: UILabel!

    func configure(with item: Item, cache: NSCache<AnyObject, AnyObject>) {
        customLabel.text = item.text

        if let image = cache.object(forKey: item.imageURL as AnyObject) as? UIImage {
            customImageView.image = image
        } else {
            DispatchQueue.global().async {
                if let data = try? Data(contentsOf: item.imageURL),
                    let image = UIImage(data: data) {
                    cache.setObject(image, forKey: item.imageURL as AnyObject)
                    DispatchQueue.main.async {
                        self.customImageView.image = image
                    }
                }
            }
        }
    }

    override func prepareForReuse() {
        super.prepareForReuse()
        customImageView.image = nil
    }
}
```

We have added a cache parameter to the **`configure`** function, which is used
to store the images that we have already loaded. If the image is already in the
cache, we use it directly. If not, we load it asynchronously on a background
thread and store it in the cache.

Additionally, we have added an implementation for the **`prepareForReuse`**
function to clear the image when the cell is reused.

Step 3: Test the app Run the app again and repeat the same steps. Notice that
the memory usage no longer keeps increasing, and the app does not crash due to a
memory issue. The problem has been fixed!

Note: This is just one way to fix a memory leak in this particular scenario.
There can be many other causes of memory leaks in iOS apps, and it's important
to understand how to identify and fix them. Additionally, testing the app
thoroughly after making any changes is crucial to ensure that the problem has
been resolved.

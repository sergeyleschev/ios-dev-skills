# Task 4

**Task:** You have a view controller that displays a list of items. The items
are fetched from an API and stored in an array property on the view controller.
When the view controller is dismissed, you notice that the array property is not
being deallocated, leading to a memory leak. Fix the memory leak.

**Solution:**

One way to fix this memory leak is to set the array property to **`nil`** in the
**`dealloc`** method of the view controller. Here's an example implementation:

```swift
class ItemListViewController: UIViewController {
    var items: [Item] = []

    deinit {
        items = nil
    }

    // Fetch items from API and display them
}
```

By setting the **`items`** property to **`nil`** in the **`dealloc`** method,
the array is deallocated when the view controller is dismissed, preventing a
memory leak. This solution assumes that the **`items`** array is only used
within the view controller and is not needed outside of it. If the **`items`**
array is needed elsewhere in the app, a different solution may be required.

# Task 5

Task: You have a view controller with a collection view that displays images.
Each cell in the collection view displays an image downloaded from a URL. The
collection view has a memory leak that needs to be fixed. Identify the cause of
the memory leak and provide a solution to fix it.

Solution: The memory leak is caused by not properly recycling cells in the
collection view. To fix the memory leak, implement the **`prepareForReuse()`**
method in the UICollectionViewCell subclass and reset any properties that need
to be reset. For example, if the cell contains an image view, set its
**`image`** property to nil. This will ensure that the cell is properly recycled
and any references to its previous content are removed from memory.

Here's an example implementation of the **`prepareForReuse()`** method:

```swift
class ImageCollectionViewCell: UICollectionViewCell {
    @IBOutlet weak var imageView: UIImageView!

    override func prepareForReuse() {
        super.prepareForReuse()
        imageView.image = nil
    }
}
```

By properly recycling cells, the memory leak should be resolved and the app's
performance should improve.

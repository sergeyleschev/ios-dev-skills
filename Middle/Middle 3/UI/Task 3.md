# Task 3

Task: Create a custom collection view layout that displays cells in a circular
pattern. The cells should be evenly spaced around the circle and centered in the
collection view.

Solution:

To create a circular collection view layout, we can subclass
UICollectionViewLayout and override the layoutAttributesForElements(in:) and
prepare() methods. Here's an example implementation:

```swift
class CircularCollectionViewLayout: UICollectionViewLayout {

    private var itemAttributes = [UICollectionViewLayoutAttributes]()
    private var center = CGPoint.zero
    private var radius: CGFloat = 0

    override func prepare() {
        super.prepare()

        guard let collectionView = collectionView else { return }

        let itemCount = collectionView.numberOfItems(inSection: 0)
        let anglePerItem = 2 * CGFloat.pi / CGFloat(itemCount)

        center = CGPoint(x: collectionView.bounds.midX, y: collectionView.bounds.midY)
        radius = min(collectionView.bounds.width, collectionView.bounds.height) / 2

        itemAttributes.removeAll()

        for i in 0..<itemCount {
            let indexPath = IndexPath(item: i, section: 0)
            let attributes = UICollectionViewLayoutAttributes(forCellWith: indexPath)

            attributes.size = CGSize(width: 50, height: 50)
            attributes.center = CGPoint(x: center.x + radius * cos(anglePerItem * CGFloat(i)),
                                        y: center.y + radius * sin(anglePerItem * CGFloat(i)))
            itemAttributes.append(attributes)
        }
    }

    override func layoutAttributesForElements(in rect: CGRect) -> [UICollectionViewLayoutAttributes]? {
        return itemAttributes.filter { rect.intersects($0.frame) }
    }

    override func layoutAttributesForItem(at indexPath: IndexPath) -> UICollectionViewLayoutAttributes? {
        return itemAttributes[indexPath.item]
    }

    override var collectionViewContentSize: CGSize {
        let itemCount = collectionView?.numberOfItems(inSection: 0) ?? 0
        let height = radius * 2 + itemSize.height
        let width = radius * 2 + itemSize.width * CGFloat(itemCount)
        return CGSize(width: width, height: height)
    }
}
```

This implementation calculates the center and radius of the circle based on the
size of the collection view, then calculates the position of each cell on the
circle using trigonometry. It also sets the size of each cell to a fixed value
of 50x50.

To use this custom layout in your collection view, simply create an instance of
the CircularCollectionViewLayout class and set it as the layout of the
collection view:

```swift
let layout = CircularCollectionViewLayout()
collectionView.collectionViewLayout = layout
```

Differences from middle 2:

-   In this task, the developer is required to create a custom collection view
    layout, which requires a deeper understanding of how collection view layouts
    work and how to override the necessary methods to achieve the desired
    layout.
-   The implementation also requires the use of trigonometry to position cells
    around a circle, which is a more complex mathematical concept than the
    previous tasks.
-   The solution is more concise and efficient, using fewer loops and
    calculations than the previous tasks.

# Task 3

Task: Implement a custom collection view layout that displays items in a
circular pattern, with each item evenly spaced around the circle. The collection
view should be scrollable horizontally.

Solution:

```swift
class CircularCollectionViewLayout: UICollectionViewLayout {
    private var cellAttributes = [UICollectionViewLayoutAttributes]()
    private var radius: CGFloat = 0
    private var centerX: CGFloat = 0
    private var centerY: CGFloat = 0
    private let itemSize = CGSize(width: 50, height: 50)

    override func prepare() {
        guard let collectionView = collectionView else { return }

        let numberOfItems = collectionView.numberOfItems(inSection: 0)
        cellAttributes.removeAll()

        radius = min(collectionView.frame.width, collectionView.frame.height) / 2
        centerX = collectionView.frame.width / 2
        centerY = collectionView.frame.height / 2

        let anglePerItem = CGFloat.pi * 2 / CGFloat(numberOfItems)

        for index in 0..<numberOfItems {
            let attribute = UICollectionViewLayoutAttributes(forCellWith: IndexPath(item: index, section: 0))
            attribute.size = itemSize

            let angle = anglePerItem * CGFloat(index)
            let xPosition = centerX + radius * cos(angle) - itemSize.width / 2
            let yPosition = centerY + radius * sin(angle) - itemSize.height / 2

            attribute.frame = CGRect(x: xPosition, y: yPosition, width: itemSize.width, height: itemSize.height)
            cellAttributes.append(attribute)
        }
    }

    override var collectionViewContentSize: CGSize {
        return CGSize(width: CGFloat(collectionView?.numberOfItems(inSection: 0) ?? 0) * itemSize.width, height: collectionView?.bounds.height ?? 0)
    }

    override func layoutAttributesForElements(in rect: CGRect) -> [UICollectionViewLayoutAttributes]? {
        return cellAttributes.filter { $0.frame.intersects(rect) }
    }

    override func layoutAttributesForItem(at indexPath: IndexPath) -> UICollectionViewLayoutAttributes? {
        return cellAttributes[indexPath.row]
    }

    override func shouldInvalidateLayout(forBoundsChange newBounds: CGRect) -> Bool {
        return true
    }
}
```

This solution implements a custom collection view layout that displays items in
a circular pattern. The **`prepare()`** method calculates the positions of each
item and stores the corresponding **`UICollectionViewLayoutAttributes`** in an
array. The **`collectionViewContentSize`** property returns the size of the
content view based on the number of items in the collection view and their size.
The **`layoutAttributesForElements(in:)`** and
**`layoutAttributesForItem(at:)`** methods return the layout attributes for the
items in the given rectangle and at the specified index path, respectively.
Finally, the **`shouldInvalidateLayout(forBoundsChange:)`** method is overridden
to ensure that the layout is invalidated when the bounds of the collection view
change. ß

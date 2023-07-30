# Task 2

Task: Develop a custom UICollectionViewLayout to display a dynamic grid of
photos. The layout should have the following features:

-   The grid should have a maximum of 3 columns, but the number of rows is
    unlimited.
-   The width of each item should be proportional to its height.
-   Items should be horizontally centered within their respective column.
-   Items in the first row should be vertically centered within their respective
    column.
-   Items in subsequent rows should be positioned directly below the item in the
    previous row with the same column index, with a minimum vertical spacing of
    10 points.
-   Items should be able to be dragged and dropped within the grid, and the
    layout should automatically update to reflect the new position of the item.

Solution:

```swift
class PhotoGridFlowLayout: UICollectionViewFlowLayout {

    private var cache: [UICollectionViewLayoutAttributes] = []

    override func prepare() {
        guard let collectionView = collectionView else { return }

        let numberOfItems = collectionView.numberOfItems(inSection: 0)
        guard numberOfItems > 0 else { return }

        let contentWidth = collectionView.bounds.width - collectionView.contentInset.left - collectionView.contentInset.right
        let availableWidth = contentWidth - minimumInteritemSpacing * 2

        let columnWidth = availableWidth / 3
        let cellWidth = columnWidth - minimumInteritemSpacing

        var xOffsets: [CGFloat] = [0, columnWidth, columnWidth * 2]
        var yOffsets: [CGFloat] = Array(repeating: CGFloat.zero, count: 3)

        for item in 0..<numberOfItems {
            let indexPath = IndexPath(item: item, section: 0)

            let height = delegate.collectionView(collectionView, heightForPhotoAtIndexPath: indexPath, withWidth: cellWidth)
            let cellFrame = CGRect(x: xOffsets[item % 3] + minimumInteritemSpacing, y: yOffsets[item % 3], width: cellWidth, height: height)
            let attributes = UICollectionViewLayoutAttributes(forCellWith: indexPath)
            attributes.frame = cellFrame
            cache.append(attributes)

            yOffsets[item % 3] = cellFrame.maxY + minimumLineSpacing

            if item % 3 == 0 {
                yOffsets = Array(repeating: yOffsets.max()!, count: 3)
            }
        }
    }

    override func layoutAttributesForElements(in rect: CGRect) -> [UICollectionViewLayoutAttributes]? {
        return cache.filter { $0.frame.intersects(rect) }
    }

    override func layoutAttributesForItem(at indexPath: IndexPath) -> UICollectionViewLayoutAttributes? {
        return cache[indexPath.item]
    }

    override func shouldInvalidateLayout(forBoundsChange newBounds: CGRect) -> Bool {
        return true
    }

    override func targetIndexPath(forInteractivelyMovingItem previousIndexPath: IndexPath, withPosition position: CGPoint) -> IndexPath {
        guard let collectionView = collectionView else { return previousIndexPath }

        let currentCenter = CGPoint(x: position.x + collectionView.contentOffset.x, y: position.y + collectionView.contentOffset.y)
        guard let targetIndexPath = collectionView.indexPathForItem(at: currentCenter) else { return previousIndexPath }
        return targetIndexPath
    }
}
```

Differences from the Middle 2 level:

-   Developing a custom **`UICollectionViewLayout`** requires a more in-depth
    understanding of UIKit and its layout system.
-   The task involves creating a more complex layout, with a maximum of 3
    columns and variable height items that must be horizontally centered and
    positioned correctly within their column.
-   The ability to implement drag and drop functionality, including updating the
    layout dynamically, requires a solid understanding of UICollectionView's
    delegate methods and how to interact with its underlying data model.

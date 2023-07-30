# Task 5

Task: Create a custom reusable UICollectionViewFlowLayout subclass that mimics
the behavior of the iOS Photos app. The cells should be square and should have a
spacing of 1 point between them. The collection view should scroll horizontally,
and the cells should snap to their positions when scrolling stops. Additionally,
the collection view should show a scroll indicator at the bottom, and tapping on
a cell should trigger a print statement with the index path of the selected
cell.

Solution:

```swift
class PhotoFlowLayout: UICollectionViewFlowLayout {

    override func prepare() {
        super.prepare()
        minimumLineSpacing = 1
        minimumInteritemSpacing = 1
        scrollDirection = .horizontal
        sectionInset = .zero
        let availableWidth = collectionView?.bounds.width ?? 0
        let cellWidth = (availableWidth / 4) - 1
        itemSize = CGSize(width: cellWidth, height: cellWidth)
        collectionView?.decelerationRate = .fast
    }

    override func targetContentOffset(forProposedContentOffset proposedContentOffset: CGPoint, withScrollingVelocity velocity: CGPoint) -> CGPoint {
        var newOffset = proposedContentOffset
        let layout = collectionView?.collectionViewLayout as! UICollectionViewFlowLayout
        let cellWidthIncludingSpacing = layout.itemSize.width + layout.minimumLineSpacing
        let indexOfMajorCell = round((collectionView!.contentOffset.x + collectionView!.contentInset.left) / cellWidthIncludingSpacing)
        let xOffset = indexOfMajorCell * cellWidthIncludingSpacing - collectionView!.contentInset.left
        newOffset.x = xOffset
        return newOffset
    }

}
```

Differences between Middle 1 and Middle 2: For this task, a Middle 2 developer
should be able to create a custom UICollectionViewFlowLayout subclass, whereas a
Middle 1 developer might not have as much experience with creating custom layout
subclasses. Additionally, a Middle 2 developer should be able to implement the
snapping behavior of the cells, which requires more advanced knowledge of the
collection view layout system.

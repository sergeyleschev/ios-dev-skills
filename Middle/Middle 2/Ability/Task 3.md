# Task 3

Task: Implement a custom collection view layout that displays cells in a
circular pattern. The layout should have a radius of 100 and the cells should be
evenly distributed around the circle. The cells should also scale based on their
distance from the center of the circle, with cells closest to the center being
larger and cells further away being smaller. The layout should be performant,
even when displaying a large number of cells.

Solution:

```swift
class CircularCollectionViewLayout: UICollectionViewLayout {

    let itemSize = CGSize(width: 50, height: 50)
    let radius: CGFloat = 100

    var attributesList = [UICollectionViewLayoutAttributes]()

    override var collectionViewContentSize: CGSize {
        return collectionView!.bounds.size
    }

    override func prepare() {
        super.prepare()

        let centerX = collectionView!.contentOffset.x + collectionView!.bounds.width / 2
        let centerY = collectionView!.contentOffset.y + collectionView!.bounds.height / 2
        let center = CGPoint(x: centerX, y: centerY)

        let count = collectionView!.numberOfItems(inSection: 0)
        let angleStep = CGFloat.pi * 2 / CGFloat(count)

        for i in 0..<count {
            let indexPath = IndexPath(item: i, section: 0)
            let attributes = UICollectionViewLayoutAttributes(forCellWith: indexPath)

            let angle = angleStep * CGFloat(i)
            let x = center.x + radius * cos(angle) - itemSize.width / 2
            let y = center.y + radius * sin(angle) - itemSize.height / 2
            attributes.frame = CGRect(x: x, y: y, width: itemSize.width, height: itemSize.height)

            let distanceFromCenter = sqrt(pow(center.x - attributes.center.x, 2) + pow(center.y - attributes.center.y, 2))
            let scale = max(1 - distanceFromCenter / radius, 0.2)
            attributes.transform = CGAffineTransform(scaleX: scale, y: scale)

            attributesList.append(attributes)
        }
    }

    override func layoutAttributesForElements(in rect: CGRect) -> [UICollectionViewLayoutAttributes]? {
        return attributesList
    }

    override func layoutAttributesForItem(at indexPath: IndexPath) -> UICollectionViewLayoutAttributes? {
        return attributesList[indexPath.row]
    }
}
```

Differences from Middle 1:

This test task is more complex and requires a deeper understanding of custom
layout development in iOS. The developer needs to have a solid understanding of
geometry and trigonometry concepts, as well as performance considerations when
dealing with a large number of cells. The solution also involves transforming
cells based on their distance from the center of the circle, which requires more
advanced knowledge of Core Animation and CGAffineTransforms. Overall, this task
is a good indicator of a developer's ability to work with complex layout
requirements and optimize performance.

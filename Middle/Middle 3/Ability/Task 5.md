# Task 5

Task: You need to implement a feature where the user can swipe left or right on
a collection view cell to delete it. When the user swipes on a cell, it should
show a delete button on the left side of the cell, and if the user swipes
further, the cell should be removed from the collection view.

Solution:

First, we need to add a swipe gesture recognizer to each cell in the collection
view. This can be done in the **`cellForItemAt`** method:

```swift
func collectionView(_ collectionView: UICollectionView, cellForItemAt indexPath: IndexPath) -> UICollectionViewCell {
    let cell = collectionView.dequeueReusableCell(withReuseIdentifier: "Cell", for: indexPath) as! MyCollectionViewCell

    let swipeGesture = UISwipeGestureRecognizer(target: self, action: #selector(handleSwipeGesture))
    swipeGesture.direction = .left
    cell.addGestureRecognizer(swipeGesture)

    return cell
}
```

Then, we need to handle the swipe gesture in the **`handleSwipeGesture`**
method:

```swift
@objc func handleSwipeGesture(_ gestureRecognizer: UISwipeGestureRecognizer) {
    guard let cell = gestureRecognizer.view as? MyCollectionViewCell else { return }

    switch gestureRecognizer.state {
    case .began:
        // Show the delete button on the left side of the cell
        cell.showDeleteButton()
    case .changed:
        let translation = gestureRecognizer.translation(in: cell)
        // Move the cell according to the swipe gesture
        cell.transform = CGAffineTransform(translationX: translation.x, y: 0)
    case .ended:
        let translation = gestureRecognizer.translation(in: cell)
        if translation.x < -cell.frame.width / 2 {
            // The cell has been swiped far enough to delete it
            deleteCell(cell)
        } else {
            // The cell has not been swiped far enough, animate it back to its original position
            UIView.animate(withDuration: 0.2) {
                cell.transform = .identity
            }
        }
    default:
        break
    }
}
```

Finally, we need to implement the **`deleteCell`** method to remove the cell
from the collection view:

```swift
func deleteCell(_ cell: MyCollectionViewCell) {
    if let indexPath = collectionView.indexPath(for: cell) {
        collectionView.performBatchUpdates({
            // Remove the cell from the data source
            data.remove(at: indexPath.row)
            // Remove the cell from the collection view
            collectionView.deleteItems(at: [indexPath])
        }, completion: nil)
    }
}
```

Differences from Middle 2:

This task builds on the previous Middle 2 task by adding a more complex
interaction to the collection view cells. The solution involves implementing
swipe gesture recognizers and animations, which require a deeper understanding
of UIKit and its gesture handling system. Additionally, the solution involves
updating the data source and performing batch updates on the collection view,
which requires a good understanding of how collection views work under the hood.
Overall, this task tests the developer's ability to implement custom
interactions and animations in a performant and reliable way.

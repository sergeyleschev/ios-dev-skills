# Task 4

Task:

Create a custom UIView that animates its background color from red to blue and
back again indefinitely.

Solution:

1. Create a new file called **`ColorChangingView.swift`** and import UIKit.

```swift
import UIKit
```

2. Create a new class called **`ColorChangingView`** that subclasses UIView.

```swift
class ColorChangingView: UIView {

}
```

3. In the **`init`** method, set the initial background color to red and start
   the animation.

```swift
override init(frame: CGRect) {
    super.init(frame: frame)
    backgroundColor = .red
    startAnimation()
}
```

4. Add a required **`init`** method to support storyboard and xib instantiation.

```swift
required init?(coder aDecoder: NSCoder) {
    super.init(coder: aDecoder)
    backgroundColor = .red
    startAnimation()
}
```

5. Create a private method called **`startAnimation`** that uses the
   **`UIView.animate`** method to animate the background color from red to blue
   and back again indefinitely.

```swift
private func startAnimation() {
    UIView.animate(withDuration: 1.0, delay: 0.0, options: [.autoreverse, .repeat], animations: {
        self.backgroundColor = .blue
    }, completion: nil)
}
```

6. Build and run the app, and add a **`ColorChangingView`** to your view
   hierarchy to see the animation.

Differences from Senior 1 level:

-   The developer is able to create custom views by subclassing UIView and
    overriding its methods.
-   The developer knows how to use the **`UIView.animate`** method to create
    simple animations.
-   The developer is familiar with the **`required init`** method to support
    storyboard and xib instantiation.

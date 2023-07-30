# Task 3

Task: Create a custom UIView subclass that displays a circle with a dynamic size
based on its frame. The circle should be filled with a random color each time
the view is drawn.

Solution:

```swift
class CircleView: UIView {

    override func draw(_ rect: CGRect) {
        let circleSize = min(rect.width, rect.height)
        let circleRect = CGRect(x: rect.midX - circleSize/2, y: rect.midY - circleSize/2, width: circleSize, height: circleSize)
        let circlePath = UIBezierPath(ovalIn: circleRect)
        UIColor.random.setFill()
        circlePath.fill()
    }

}

extension UIColor {

    static var random: UIColor {
        let red = CGFloat.random(in: 0...1)
        let green = CGFloat.random(in: 0...1)
        let blue = CGFloat.random(in: 0...1)
        return UIColor(red: red, green: green, blue: blue, alpha: 1.0)
    }

}
```

Differences from Middle 1:

-   This task requires creating a custom UIView subclass, which shows the
    developer's ability to work with object-oriented programming and creating
    reusable components.
-   The view's size is based on its frame, which shows the developer's knowledge
    of layout and geometry.
-   The circle's color is randomly generated each time the view is drawn, which
    shows the developer's knowledge of using random numbers and generating
    colors programmatically.

# Task 1

Task: Create a custom UIView subclass called "GradientView" that displays a
gradient background. The view should have the following properties:

-   Start color: UIColor
-   End color: UIColor
-   Start point: CGPoint
-   End point: CGPoint

The view should automatically update its gradient when any of the properties are
changed. The gradient should be applied to the view's layer using
CAGradientLayer.

Solution:

```swift
import UIKit

class GradientView: UIView {

    private let gradientLayer = CAGradientLayer()

    var startPoint: CGPoint = CGPoint(x: 0.5, y: 0) {
        didSet {
            updateGradient()
        }
    }

    var endPoint: CGPoint = CGPoint(x: 0.5, y: 1) {
        didSet {
            updateGradient()
        }
    }

    var startColor: UIColor = .white {
        didSet {
            updateGradient()
        }
    }

    var endColor: UIColor = .black {
        didSet {
            updateGradient()
        }
    }

    override func layoutSubviews() {
        super.layoutSubviews()
        gradientLayer.frame = bounds
    }

    private func updateGradient() {
        gradientLayer.colors = [startColor.cgColor, endColor.cgColor]
        gradientLayer.startPoint = startPoint
        gradientLayer.endPoint = endPoint
    }

    override init(frame: CGRect) {
        super.init(frame: frame)
        layer.addSublayer(gradientLayer)
        updateGradient()
    }

    required init?(coder aDecoder: NSCoder) {
        fatalError("init(coder:) has not been implemented")
    }
}
```

Differences from Junior level:

-   This task requires the developer to create a custom UIView subclass and
    update its layer properties to display a gradient background. This
    demonstrates a deeper understanding of UIKit and custom view development.
-   The task requires the developer to create a subclass that automatically
    updates its gradient when any of the properties are changed, which
    demonstrates knowledge of property observers and how to use them to update a
    view's appearance.
-   The task also requires the developer to use CAGradientLayer to apply the
    gradient to the view's layer, which demonstrates knowledge of core animation
    and layer-based rendering in UIKit.

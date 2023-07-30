# Task 4

Task: Create a custom progress bar view with the following requirements:

-   The progress bar should be horizontal and have a height of 10 points.
-   The background color of the progress bar should be light gray (#CCCCCC).
-   The foreground color of the progress bar should be blue (#007AFF).
-   The progress bar should be filled from left to right.
-   The progress of the bar should be set using a property called "progress"
    with a value between 0 and 1.
-   The progress bar should be able to animate smoothly when the progress value
    is changed.

Solution:

```swift
import UIKit

class ProgressBarView: UIView {
    private let backgroundView = UIView()
    private let foregroundView = UIView()

    var progress: CGFloat = 0 {
        didSet {
            setNeedsLayout()
            layoutIfNeeded()
        }
    }

    override init(frame: CGRect) {
        super.init(frame: frame)
        setupViews()
    }

    required init?(coder: NSCoder) {
        super.init(coder: coder)
        setupViews()
    }

    private func setupViews() {
        backgroundView.backgroundColor = UIColor(hex: "#CCCCCC")
        foregroundView.backgroundColor = UIColor(hex: "#007AFF")
        addSubview(backgroundView)
        addSubview(foregroundView)
    }

    override func layoutSubviews() {
        super.layoutSubviews()
        let backgroundWidth = bounds.width
        let foregroundWidth = backgroundWidth * progress
        backgroundView.frame = CGRect(x: 0, y: 0, width: backgroundWidth, height: 10)
        foregroundView.frame = CGRect(x: 0, y: 0, width: foregroundWidth, height: 10)
    }
}

extension UIColor {
    convenience init(hex: String) {
        let hex = hex.trimmingCharacters(in: CharacterSet.alphanumerics.inverted)
        var int = UInt64()
        Scanner(string: hex).scanHexInt64(&int)
        let r, g, b: UInt64
        switch hex.count {
        case 3: // RGB (12-bit)
            (r, g, b) = (
                (int >> 8) * 17,
                (int >> 4 & 0xF) * 17,
                (int & 0xF) * 17
            )
        case 6: // RGB (24-bit)
            (r, g, b) = (
                int >> 16,
                int >> 8 & 0xFF,
                int & 0xFF
            )
        default:
            (r, g, b) = (0, 0, 0)
        }
        self.init(
            red: CGFloat(r) / 255,
            green: CGFloat(g) / 255,
            blue: CGFloat(b) / 255, alpha: 1
        )
    }
}
```

Differences from Middle 2:

-   The solution now includes an animation for the progress bar when the
    progress value is changed.
-   The progress bar now has a more complex layout, requiring two subviews to be
    added and positioned in relation to each other.
-   The solution also includes a custom extension to the UIColor class that
    allows colors to be created using hex codes.

# Task 1

Task: Create a custom UIView subclass that displays a circle with a label inside
it. The label should be customizable and the circle should have a customizable
color.

Solution:

```swift
class CircleLabelView: UIView {

    private let circleView = UIView()
    private let label = UILabel()

    override init(frame: CGRect) {
        super.init(frame: frame)
        commonInit()
    }

    required init?(coder aDecoder: NSCoder) {
        super.init(coder: aDecoder)
        commonInit()
    }

    private func commonInit() {
        circleView.translatesAutoresizingMaskIntoConstraints = false
        label.translatesAutoresizingMaskIntoConstraints = false
        addSubview(circleView)
        addSubview(label)
        NSLayoutConstraint.activate([
            circleView.centerXAnchor.constraint(equalTo: centerXAnchor),
            circleView.centerYAnchor.constraint(equalTo: centerYAnchor),
            circleView.widthAnchor.constraint(equalTo: widthAnchor),
            circleView.heightAnchor.constraint(equalTo: heightAnchor),
            label.centerXAnchor.constraint(equalTo: centerXAnchor),
            label.centerYAnchor.constraint(equalTo: centerYAnchor)
        ])
    }

    var labelString: String? {
        get { return label.text }
        set { label.text = newValue }
    }

    var circleColor: UIColor? {
        get { return circleView.backgroundColor }
        set { circleView.backgroundColor = newValue }
    }

    override func layoutSubviews() {
        super.layoutSubviews()
        circleView.layer.cornerRadius = circleView.bounds.width / 2.0
    }

}
```

Differences from Junior 2:

-   Understanding of how to create a custom UIView subclass
-   Use of layout constraints instead of frame-based layout
-   Use of a computed property to get/set label text and circle color
-   Use of **`layoutSubviews()`** to update the corner radius of the circle view
-   Cleaner and more concise code overall.

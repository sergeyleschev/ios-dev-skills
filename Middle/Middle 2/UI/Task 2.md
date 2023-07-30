# Task 2

Task: Create a custom UIButton subclass that has a gradient background color and
a rounded corner border.

Solution:

```swift
class GradientButton: UIButton {

    private var gradientLayer: CAGradientLayer!
    private var startColor: UIColor!
    private var endColor: UIColor!
    private var cornerRadius: CGFloat!

    convenience init(startColor: UIColor, endColor: UIColor, cornerRadius: CGFloat) {
        self.init(frame: .zero)
        self.startColor = startColor
        self.endColor = endColor
        self.cornerRadius = cornerRadius
        setupView()
    }

    override func layoutSubviews() {
        super.layoutSubviews()
        gradientLayer.frame = bounds
    }

    private func setupView() {
        gradientLayer = CAGradientLayer()
        gradientLayer.colors = [startColor.cgColor, endColor.cgColor]
        gradientLayer.locations = [0, 1]
        gradientLayer.startPoint = CGPoint(x: 0, y: 0)
        gradientLayer.endPoint = CGPoint(x: 1, y: 1)
        layer.insertSublayer(gradientLayer, at: 0)
        layer.cornerRadius = cornerRadius
        clipsToBounds = true
    }

}

```

To use this custom button, you can create an instance and add it to your view
hierarchy like this:

```swift
let gradientButton = GradientButton(startColor: .red, endColor: .orange, cornerRadius: 10)
gradientButton.setTitle("Gradient Button", for: .normal)
gradientButton.setTitleColor(.white, for: .normal)
gradientButton.titleLabel?.font = UIFont.systemFont(ofSize: 20, weight: .bold)
gradientButton.translatesAutoresizingMaskIntoConstraints = false
view.addSubview(gradientButton)
NSLayoutConstraint.activate([
    gradientButton.centerXAnchor.constraint(equalTo: view.centerXAnchor),
    gradientButton.centerYAnchor.constraint(equalTo: view.centerYAnchor),
    gradientButton.widthAnchor.constraint(equalToConstant: 200),
    gradientButton.heightAnchor.constraint(equalToConstant: 50)
])
```

Differences from Middle 1: This task requires creating a custom subclass of
UIButton with a gradient background color and rounded corner border. It requires
knowledge of Core Animation and how to create and add a CAGradientLayer to a
view's layer hierarchy. The use of a convenience initializer and overriding the
**`layoutSubviews()`** method shows a deeper understanding of the view lifecycle
and how to handle view layout.

# Task 4

Task: You are building a new feature for an app and need to create a custom user
interface element that cannot be easily achieved using Interface Builder. Write
the code to create a custom UIView subclass that satisfies the following
requirements:

-   The view should be circular with a border width of 2 and a border color of
    red.
-   The view should have a label centered inside it that displays the text
    "Hello, World!".
-   The view's layout should be done programmatically using autolayout
    constraints.

Solution:

```swift
class CustomView: UIView {

    private let label: UILabel = {
        let label = UILabel()
        label.text = "Hello, World!"
        label.textAlignment = .center
        label.translatesAutoresizingMaskIntoConstraints = false
        return label
    }()

    override init(frame: CGRect) {
        super.init(frame: frame)

        self.layer.borderWidth = 2
        self.layer.borderColor = UIColor.red.cgColor
        self.layer.cornerRadius = self.bounds.size.width / 2

        self.addSubview(label)
        NSLayoutConstraint.activate([
            label.centerXAnchor.constraint(equalTo: self.centerXAnchor),
            label.centerYAnchor.constraint(equalTo: self.centerYAnchor),
        ])
    }

    required init?(coder aDecoder: NSCoder) {
        fatalError("init(coder:) has not been implemented")
    }
}
```

Differences from Junior 3 level:

The main difference between a Junior 3 and Middle 1 developer is that the latter
is expected to have a deeper understanding of iOS development concepts and the
ability to create custom UI elements programmatically using autolayout
constraints. In this task, the candidate is required to build a custom view
subclass using code that implements specific UI requirements. Additionally, the
solution is expected to be more efficient and performant than a Junior-level
solution.

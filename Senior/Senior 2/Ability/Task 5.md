# Task 5

Task: Implement a reusable "loading" view that can be used throughout the app.
The view should have a customizable message and color scheme. It should also
support an optional animation to indicate activity.

Solution:

```swift
import UIKit

class LoadingView: UIView {

    private let activityIndicatorView = UIActivityIndicatorView(style: .large)
    private let messageLabel = UILabel()

    override init(frame: CGRect) {
        super.init(frame: frame)

        // Set up activity indicator view
        activityIndicatorView.translatesAutoresizingMaskIntoConstraints = false
        activityIndicatorView.color = .gray
        addSubview(activityIndicatorView)
        NSLayoutConstraint.activate([
            activityIndicatorView.centerXAnchor.constraint(equalTo: centerXAnchor),
            activityIndicatorView.centerYAnchor.constraint(equalTo: centerYAnchor),
        ])

        // Set up message label
        messageLabel.translatesAutoresizingMaskIntoConstraints = false
        messageLabel.font = UIFont.systemFont(ofSize: 16)
        messageLabel.textColor = .gray
        messageLabel.textAlignment = .center
        addSubview(messageLabel)
        NSLayoutConstraint.activate([
            messageLabel.centerXAnchor.constraint(equalTo: centerXAnchor),
            messageLabel.topAnchor.constraint(equalTo: activityIndicatorView.bottomAnchor, constant: 8),
            messageLabel.leadingAnchor.constraint(greaterThanOrEqualTo: leadingAnchor, constant: 16),
            messageLabel.trailingAnchor.constraint(lessThanOrEqualTo: trailingAnchor, constant: -16),
            messageLabel.bottomAnchor.constraint(lessThanOrEqualTo: bottomAnchor),
        ])
    }

    required init?(coder: NSCoder) {
        fatalError("init(coder:) has not been implemented")
    }

    func startAnimating() {
        activityIndicatorView.startAnimating()
    }

    func stopAnimating() {
        activityIndicatorView.stopAnimating()
    }

    func setMessage(_ message: String) {
        messageLabel.text = message
    }

    func setColorScheme(_ color: UIColor) {
        activityIndicatorView.color = color
        messageLabel.textColor = color
    }
}
```

To use the view, create an instance of **`LoadingView`** and add it to the view
hierarchy. You can customize the message and color scheme using the
**`setMessage`** and **`setColorScheme`** methods, respectively. To start and
stop the activity animation, use the **`startAnimating`** and
**`stopAnimating`** methods.

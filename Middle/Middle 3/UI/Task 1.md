# Task 1

Task: Create a custom view that displays a progress indicator with a label
showing the percentage complete. The view should have a method to update the
progress percentage and animate the progress indicator to the new value. Use
auto-layout code to position the UI elements correctly on different screen
sizes.

Solution:

```swift
import UIKit

class ProgressView: UIView {

    let progressLabel: UILabel = {
        let label = UILabel()
        label.translatesAutoresizingMaskIntoConstraints = false
        label.text = "0%"
        return label
    }()

    let progressView: UIProgressView = {
        let progressView = UIProgressView()
        progressView.translatesAutoresizingMaskIntoConstraints = false
        progressView.progress = 0
        return progressView
    }()

    override init(frame: CGRect) {
        super.init(frame: frame)
        setupView()
    }

    required init?(coder aDecoder: NSCoder) {
        super.init(coder: aDecoder)
        setupView()
    }

    private func setupView() {
        backgroundColor = .white

        addSubview(progressLabel)
        addSubview(progressView)

        NSLayoutConstraint.activate([
            progressLabel.centerXAnchor.constraint(equalTo: centerXAnchor),
            progressLabel.centerYAnchor.constraint(equalTo: centerYAnchor, constant: -20),

            progressView.centerXAnchor.constraint(equalTo: centerXAnchor),
            progressView.topAnchor.constraint(equalTo: progressLabel.bottomAnchor, constant: 20),
            progressView.widthAnchor.constraint(equalToConstant: 200),
            progressView.heightAnchor.constraint(equalToConstant: 20)
        ])
    }

    func updateProgress(percentComplete: Float, animated: Bool) {
        progressLabel.text = "\(Int(percentComplete * 100))%"
        progressView.setProgress(percentComplete, animated: animated)
    }

}
```

Differences from Middle level 2:

-   The solution creates a custom view to encapsulate the progress indicator and
    label, instead of using separate UI elements in a view controller.
-   The solution animates the progress indicator when updating the progress
    percentage.
-   The solution includes a method to update the progress percentage, taking a
    parameter for whether the update should be animated or not.

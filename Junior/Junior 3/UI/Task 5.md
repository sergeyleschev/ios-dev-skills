# Task 5

Task: Create a custom view that displays a progress bar with a label indicating
the percentage of completion.

Solution:

```swift
import UIKit

class ProgressBarView: UIView {

    let progressBar = UIProgressView()
    let percentageLabel = UILabel()

    override init(frame: CGRect) {
        super.init(frame: frame)
        setupView()
    }

    required init?(coder: NSCoder) {
        fatalError("init(coder:) has not been implemented")
    }

    private func setupView() {
        // Set progress bar properties
        progressBar.translatesAutoresizingMaskIntoConstraints = false
        progressBar.progressTintColor = .blue
        progressBar.trackTintColor = .gray
        addSubview(progressBar)

        // Set percentage label properties
        percentageLabel.translatesAutoresizingMaskIntoConstraints = false
        percentageLabel.textAlignment = .center
        percentageLabel.textColor = .black
        addSubview(percentageLabel)

        // Set constraints
        NSLayoutConstraint.activate([
            progressBar.leadingAnchor.constraint(equalTo: leadingAnchor, constant: 20),
            progressBar.trailingAnchor.constraint(equalTo: trailingAnchor, constant: -20),
            progressBar.centerYAnchor.constraint(equalTo: centerYAnchor),

            percentageLabel.centerXAnchor.constraint(equalTo: centerXAnchor),
            percentageLabel.centerYAnchor.constraint(equalTo: centerYAnchor)
        ])
    }

    func setProgress(_ progress: Float) {
        progressBar.setProgress(progress, animated: true)
        let percentage = Int(progress * 100)
        percentageLabel.text = "\(percentage)%"
    }
}
```

To use this view, create an instance of it and add it as a subview to your
parent view. Then call the **`setProgress`** method with the progress value you
want to display.

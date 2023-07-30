# Task 3

Task: You have been given a requirement to create a custom table view cell with
a specific layout that cannot be achieved using the default styles. Write a code
to create a custom table view cell programmatically with autolayout constraints.

Solution:

```swift
class CustomTableViewCell: UITableViewCell {
    let titleLabel = UILabel()
    let subtitleLabel = UILabel()
    let thumbnailImageView = UIImageView()

    override init(style: UITableViewCell.CellStyle, reuseIdentifier: String?) {
        super.init(style: style, reuseIdentifier: reuseIdentifier)

        addSubview(titleLabel)
        addSubview(subtitleLabel)
        addSubview(thumbnailImageView)

        titleLabel.translatesAutoresizingMaskIntoConstraints = false
        subtitleLabel.translatesAutoresizingMaskIntoConstraints = false
        thumbnailImageView.translatesAutoresizingMaskIntoConstraints = false

        NSLayoutConstraint.activate([
            thumbnailImageView.leadingAnchor.constraint(equalTo: leadingAnchor, constant: 16),
            thumbnailImageView.topAnchor.constraint(equalTo: topAnchor, constant: 16),
            thumbnailImageView.bottomAnchor.constraint(equalTo: bottomAnchor, constant: -16),
            thumbnailImageView.widthAnchor.constraint(equalToConstant: 80),

            titleLabel.leadingAnchor.constraint(equalTo: thumbnailImageView.trailingAnchor, constant: 16),
            titleLabel.trailingAnchor.constraint(equalTo: trailingAnchor, constant: -16),
            titleLabel.topAnchor.constraint(equalTo: topAnchor, constant: 16),

            subtitleLabel.leadingAnchor.constraint(equalTo: thumbnailImageView.trailingAnchor, constant: 16),
            subtitleLabel.trailingAnchor.constraint(equalTo: trailingAnchor, constant: -16),
            subtitleLabel.topAnchor.constraint(equalTo: titleLabel.bottomAnchor, constant: 8),
            subtitleLabel.bottomAnchor.constraint(equalTo: bottomAnchor, constant: -16)
        ])
    }

    required init?(coder aDecoder: NSCoder) {
        fatalError("init(coder:) has not been implemented")
    }
}
```

Differences from Junior Level 3:

The key difference between Junior Level 3 and Middle Level 1 is the ability to
make informed decisions about when to use Interface Builder and when to build UI
in code. A Middle Level 1 iOS developer would have a deeper understanding of the
advantages and disadvantages of each approach and would be able to choose the
appropriate method based on the specific requirements of the project. In this
task, the developer is required to build a custom table view cell
programmatically using autolayout constraints, which is an example of when
building UI in code can be beneficial. Additionally, the Middle Level 1
developer would be expected to have a more comprehensive understanding of
autolayout constraints and be able to create more complex UI layouts
programmatically.

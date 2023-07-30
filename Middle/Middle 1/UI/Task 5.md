# Task 5

Task: Create a custom view that displays a user profile image and name, with the
ability to edit the name by tapping on it. The view should be created in code
using autolayout, and should be reusable across different screens and view
controllers. Use the following requirements:

-   The user profile image should be displayed in a circular frame with a
    border.
-   The user's name should be displayed in a UILabel, centered below the profile
    image.
-   Tapping on the name label should present a UIAlertController with a text
    field to edit the name.
-   The view should have a height of 150 points, and should stretch horizontally
    to fill the parent view.

Solution:

```swift
class UserProfileView: UIView {

    // MARK: - Properties

    private let profileImageView: UIImageView = {
        let imageView = UIImageView()
        imageView.contentMode = .scaleAspectFit
        imageView.layer.borderWidth = 2
        imageView.layer.borderColor = UIColor.black.cgColor
        imageView.layer.cornerRadius = 50
        imageView.layer.masksToBounds = true
        imageView.translatesAutoresizingMaskIntoConstraints = false
        return imageView
    }()

    private let nameLabel: UILabel = {
        let label = UILabel()
        label.textAlignment = .center
        label.textColor = .black
        label.font = UIFont.boldSystemFont(ofSize: 20)
        label.translatesAutoresizingMaskIntoConstraints = false
        return label
    }()

    // MARK: - Initialization

    override init(frame: CGRect) {
        super.init(frame: frame)
        setupViews()
    }

    required init?(coder: NSCoder) {
        fatalError("init(coder:) has not been implemented")
    }

    // MARK: - View Setup

    private func setupViews() {
        addSubview(profileImageView)
        addSubview(nameLabel)

        NSLayoutConstraint.activate([
            profileImageView.topAnchor.constraint(equalTo: topAnchor, constant: 16),
            profileImageView.centerXAnchor.constraint(equalTo: centerXAnchor),
            profileImageView.widthAnchor.constraint(equalToConstant: 100),
            profileImageView.heightAnchor.constraint(equalToConstant: 100),

            nameLabel.topAnchor.constraint(equalTo: profileImageView.bottomAnchor, constant: 16),
            nameLabel.centerXAnchor.constraint(equalTo: centerXAnchor),
            nameLabel.leadingAnchor.constraint(equalTo: leadingAnchor, constant: 8),
            nameLabel.trailingAnchor.constraint(equalTo: trailingAnchor, constant: -8),
            nameLabel.bottomAnchor.constraint(equalTo: bottomAnchor, constant: -16),
        ])

        let tapGesture = UITapGestureRecognizer(target: self, action: #selector(nameLabelTapped))
        nameLabel.addGestureRecognizer(tapGesture)
        nameLabel.isUserInteractionEnabled = true
    }

    // MARK: - Public Methods

    func configure(with profileImage: UIImage?, name: String) {
        profileImageView.image = profileImage
        nameLabel.text = name
    }

    // MARK: - Private Methods

    @objc private func nameLabelTapped() {
        let alert = UIAlertController(title: "Edit Name", message: nil, preferredStyle: .alert)
        alert.addTextField { textField in
            textField.placeholder = "Enter Name"
        }
        alert.addAction(UIAlertAction(title: "Cancel", style: .cancel, handler: nil))
        alert.addAction(UIAlertAction(title: "Save", style: .default, handler: { [weak self] action in
            guard let textField = alert.textFields?.first else { return }
            self?.nameLabel.text = textField.text
        }))
        UIApplication.shared.windows.first?.rootViewController?.present(alert, animated: true, completion: nil)
    }
}
```

Differences from Junior 3 level:

-   This task involves creating a custom view in code, rather than using
    Interface Builder.
-   The view is designed to be reusable across different screens and view
    controllers, indicating a higher level of architectural understanding.
-   The task involves

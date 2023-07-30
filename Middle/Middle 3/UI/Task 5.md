# Task 5

Task: Create a custom control that displays a rating (out of 5 stars) using a
UIView subclass. The control should be initialized with a rating value (between
0 and 5), and should allow the user to tap on the control to update the rating.
The control should also support updating the rating programatically.

Solution:

```swift
class RatingControl: UIView {

    private let maxRating = 5
    private let spacing = 5
    private var rating = 0 {
        didSet {
            setNeedsLayout()
        }
    }
    private var ratingButtons = [UIButton]()

    override init(frame: CGRect) {
        super.init(frame: frame)
        setupButtons()
    }

    required init?(coder: NSCoder) {
        super.init(coder: coder)
        setupButtons()
    }

    private func setupButtons() {
        for _ in 0..<maxRating {
            let button = UIButton()
            button.addTarget(self, action: #selector(ratingButtonTapped(button:)), for: .touchUpInside)
            ratingButtons.append(button)
            addSubview(button)
        }
    }

    override func layoutSubviews() {
        super.layoutSubviews()
        let buttonSize = Int(frame.size.height)
        var buttonFrame = CGRect(x: 0, y: 0, width: buttonSize, height: buttonSize)
        for (index, button) in ratingButtons.enumerated() {
            buttonFrame.origin.x = CGFloat(index * (buttonSize + spacing))
            button.frame = buttonFrame
            let image = index < rating ? UIImage(named: "filledStar") : UIImage(named: "emptyStar")
            button.setImage(image, for: .normal)
        }
    }

    @objc func ratingButtonTapped(button: UIButton) {
        guard let index = ratingButtons.firstIndex(of: button) else { return }
        let selectedRating = index + 1
        if selectedRating == rating {
            rating = 0
        } else {
            rating = selectedRating
        }
    }

    func setRating(_ rating: Int) {
        self.rating = rating
    }

    func getRating() -> Int {
        return rating
    }
}
```

Differences from Middle 2 level:

This task requires the developer to create a custom control, which involves more
advanced knowledge of UI and view programming. The solution includes creating a
custom UIView subclass, using UIButton instances to represent each star rating,
implementing touch handling to allow user interaction, and supporting
programmatic updates to the rating value. The code also includes better
organization and separation of concerns, with private properties and methods for
internal use, and clear method names and documentation for readability.

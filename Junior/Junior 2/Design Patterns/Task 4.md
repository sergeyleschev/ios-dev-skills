# Task 4

Task: Create a custom UIButton subclass that changes its background color when
tapped using Target-Action pattern.

Solution:

First, create a new subclass of UIButton:

```swift
class TappableButton: UIButton {

    override init(frame: CGRect) {
        super.init(frame: frame)
        addTarget(self, action: #selector(buttonTapped), for: .touchUpInside)
    }

    required init?(coder aDecoder: NSCoder) {
        super.init(coder: aDecoder)
        addTarget(self, action: #selector(buttonTapped), for: .touchUpInside)
    }

    @objc func buttonTapped() {
        backgroundColor = UIColor.red // Change background color when tapped
    }
}
```

Then, in your view controller, you can create an instance of this button and add
it to your view:

```swift
let tappableButton = TappableButton(frame: CGRect(x: 0, y: 0, width: 100, height: 50))
tappableButton.setTitle("Tap me", for: .normal)
tappableButton.backgroundColor = UIColor.blue
view.addSubview(tappableButton)
```

Differences between Junior 1 and Junior 2 level of developers:

-   In Junior 2, the developer should have a better understanding of the
    Target-Action pattern and its implementation in UIKit.
-   The code solution should be more concise and organized, and can demonstrate
    the use of protocols and extensions to make the code more reusable and
    modular.
-   The developer should also have an understanding of the different types of
    controls in UIKit that support Target-Action pattern, such as UISlider and
    UISwitch, and how to customize them to fit the needs of their app.

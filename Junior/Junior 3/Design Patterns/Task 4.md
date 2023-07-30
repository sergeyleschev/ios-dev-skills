# Task 4

Task: Create a custom UISlider subclass that implements the target-action
pattern. When the slider value changes, it should print the new value to the
console using the target-action pattern.

Solution:

```swift
import UIKit

class CustomSlider: UISlider {

    override init(frame: CGRect) {
        super.init(frame: frame)
        self.addTarget(self, action: #selector(sliderValueChanged(_:)), for: .valueChanged)
    }

    required init?(coder aDecoder: NSCoder) {
        super.init(coder: aDecoder)
        self.addTarget(self, action: #selector(sliderValueChanged(_:)), for: .valueChanged)
    }

    @objc func sliderValueChanged(_ sender: UISlider) {
        print("Slider value: \(sender.value)")
    }
}
```

Differences between Junior 2 and Junior 3 levels:

At the Junior 3 level, a developer should have a deeper understanding of the
target-action pattern and how to implement it in custom classes. They should be
able to explain the purpose and benefits of target-action in iOS development.
Additionally, they should be able to identify situations where target-action is
appropriate and where other design patterns may be more suitable. They should
also be familiar with other types of controls that can use target-action, such
as UISwitch and UIStepper.

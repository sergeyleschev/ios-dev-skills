# Task 3

Task: Create a custom UIButton subclass that implements the target-action
pattern. When the button is tapped, it should change its title to "Tapped" and
print "Button tapped" to the console.

Solution:

```swift
import UIKit

class CustomButton: UIButton {

    override init(frame: CGRect) {
        super.init(frame: frame)
        self.addTarget(self, action: #selector(buttonTapped(_:)), for: .touchUpInside)
        self.setTitle("Tap me", for: .normal)
    }

    required init?(coder aDecoder: NSCoder) {
        super.init(coder: aDecoder)
        self.addTarget(self, action: #selector(buttonTapped(_:)), for: .touchUpInside)
        self.setTitle("Tap me", for: .normal)
    }

    @objc func buttonTapped(_ sender: UIButton) {
        self.setTitle("Tapped", for: .normal)
        print("Button tapped")
    }
}
```

Differences between Junior 2 and Junior 3 levels:

At the Junior 3 level, a developer should have a deeper understanding of the
target-action pattern and how to implement it in custom classes. They should be
able to explain the purpose and benefits of target-action in iOS development.
Additionally, they should be able to identify situations where target-action is
appropriate and where other design patterns may be more suitable. They should
also be familiar with other types of events that can be used with target-action,
such as UIControl.Event.valueChanged.

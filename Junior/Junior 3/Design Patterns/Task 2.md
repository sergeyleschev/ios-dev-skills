# Task 2

Task: Create a custom UITextField subclass that implements the
UITextFieldDelegate protocol. The text field should have a placeholder of "Enter
text here". When the user types in the text field, it should print the entered
text to the console using the delegate method textFieldDidEndEditing(\_:).

Solution:

```swift
import UIKit

class CustomTextField: UITextField, UITextFieldDelegate {

    override init(frame: CGRect) {
        super.init(frame: frame)
        self.delegate = self
        self.placeholder = "Enter text here"
    }

    required init?(coder aDecoder: NSCoder) {
        super.init(coder: aDecoder)
        self.delegate = self
        self.placeholder = "Enter text here"
    }

    func textFieldDidEndEditing(_ textField: UITextField) {
        if let enteredText = textField.text {
            print("Entered text: \(enteredText)")
        }
    }
}
```

Differences between Junior 2 and Junior 3 levels:

At the Junior 3 level, a developer should have a deeper understanding of the
delegation pattern and how to implement it in custom classes. They should be
able to explain the purpose and benefits of delegation in iOS development.
Additionally, they should be able to identify situations where delegation is
appropriate and where other design patterns may be more suitable.

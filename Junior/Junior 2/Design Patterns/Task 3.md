# Task 3

Task: Create a simple custom button class with a title and an action that will
be called when the button is tapped using Target-Action pattern. The action
should be defined outside of the button class and should accept the button
instance as a parameter.

Solution:

```swift
import UIKit

class CustomButton: UIButton {
    var tapAction: ((CustomButton) -> Void)?

    init(title: String) {
        super.init(frame: .zero)
        setTitle(title, for: .normal)
        addTarget(self, action: #selector(buttonTapped), for: .touchUpInside)
    }

    required init?(coder: NSCoder) {
        fatalError("init(coder:) has not been implemented")
    }

    @objc func buttonTapped() {
        tapAction?(self)
    }
}

// Example usage
class ViewController: UIViewController {
    override func viewDidLoad() {
        super.viewDidLoad()

        let customButton = CustomButton(title: "Tap me!")
        customButton.tapAction = { button in
            print("Button tapped: \(button.titleLabel?.text ?? "")")
        }

        view.addSubview(customButton)
        customButton.translatesAutoresizingMaskIntoConstraints = false
        NSLayoutConstraint.activate([
            customButton.centerXAnchor.constraint(equalTo: view.centerXAnchor),
            customButton.centerYAnchor.constraint(equalTo: view.centerYAnchor),
        ])
    }
}
```

In this solution, we have created a custom button class **`CustomButton`** with
a **`tapAction`** property, which is a closure that accepts an instance of
**`CustomButton`** as a parameter and returns **`Void`**. The closure is called
when the button is tapped. We have also overridden the **`init(title:)`** method
to set the button's title and add the target-action pair. In the
**`buttonTapped()`** method, we call the **`tapAction`** closure with the
**`self`** parameter.

In the example usage in the **`ViewController`**, we create an instance of
**`CustomButton`** and set its **`tapAction`** closure to print a message when
the button is tapped. We add the button to the view and constrain it to the
center of the view.

The key difference from the previous task is that this task requires
understanding of the Target-Action pattern instead of the delegation pattern.
Additionally, the implementation of the **`CustomButton`** class requires adding
a closure property and calling it when the button is tapped, instead of calling
a delegate method.

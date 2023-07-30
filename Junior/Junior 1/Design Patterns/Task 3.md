# Task 3

Task:

Create a simple iOS app that contains a button, a label, and a text field. When
the user taps the button, the text in the text field should be displayed in the
label. Use Target-Action design pattern to implement this functionality.

Solution:

To implement this functionality using the Target-Action design pattern, we need
to follow these steps:

1. Create a new Xcode project and choose the Single View App template.
2. Delete the Main.storyboard file and remove the reference to it from the
   Info.plist file.
3. Create a new UIView subclass for the view controller's view and add the
   button, label, and text field programmatically in the viewDidLoad method.
4. Create a new method in the view controller that will be called when the
   button is tapped. This method should read the text from the text field and
   set it as the label's text.
5. Use addTarget method of UIButton class to add the target-action pattern to
   the button. Pass the view controller instance as the target and the new
   method as the action.

Here's the complete code:

```swift
import UIKit

class ViewController: UIViewController {

    let label = UILabel()
    let textField = UITextField()
    let button = UIButton(type: .system)

    override func viewDidLoad() {
        super.viewDidLoad()

        view.addSubview(label)
        view.addSubview(textField)
        view.addSubview(button)

        textField.borderStyle = .roundedRect

        label.textAlignment = .center
        label.text = "Label"

        button.setTitle("Update", for: .normal)

        button.addTarget(self, action: #selector(buttonTapped), for: .touchUpInside)

        setupLayout()
    }

    func setupLayout() {
        label.translatesAutoresizingMaskIntoConstraints = false
        textField.translatesAutoresizingMaskIntoConstraints = false
        button.translatesAutoresizingMaskIntoConstraints = false

        NSLayoutConstraint.activate([
            textField.centerXAnchor.constraint(equalTo: view.centerXAnchor),
            textField.centerYAnchor.constraint(equalTo: view.centerYAnchor, constant: -50),
            textField.widthAnchor.constraint(equalToConstant: 200),

            label.topAnchor.constraint(equalTo: textField.bottomAnchor, constant: 20),
            label.centerXAnchor.constraint(equalTo: view.centerXAnchor),
            label.widthAnchor.constraint(equalToConstant: 200),

            button.topAnchor.constraint(equalTo: label.bottomAnchor, constant: 20),
            button.centerXAnchor.constraint(equalTo: view.centerXAnchor),
        ])
    }

    @objc func buttonTapped() {
        label.text = textField.text
    }
}

```

This code creates a view controller with a label, a text field, and a button.
When the button is tapped, the text from the text field is displayed in the
label using the Target-Action design pattern.

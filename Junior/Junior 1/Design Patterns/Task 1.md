# Task 1

Task: Create a simple app that uses Delegation to pass data between two View
Controllers.

Solution:

First, let's create a new Xcode project and add two View Controllers to the
storyboard. The first View Controller will contain a text field and a button,
while the second View Controller will contain a label to display the text
entered in the text field.

Next, create a protocol called **`TextFieldDelegate`** that defines a method to
pass the text entered in the text field to the second View Controller:

```swift
protocol TextFieldDelegate {
    func didEnterText(_ text: String)
}
```

In the first View Controller, create a variable of type **`TextFieldDelegate`**:

```swift
var delegate: TextFieldDelegate?
```

When the button is tapped, call the delegate method passing in the text entered
in the text field:

```swift
@IBAction func buttonTapped(_ sender: UIButton) {
    guard let text = textField.text else { return }
    delegate?.didEnterText(text)
}
```

In the second View Controller, implement the **`TextFieldDelegate`** protocol
and set the first View Controller as the delegate:

```swift
class SecondViewController: UIViewController, TextFieldDelegate {

    func didEnterText(_ text: String) {
        label.text = text
    }

    override func prepare(for segue: UIStoryboardSegue, sender: Any?) {
        if let firstViewController = segue.source as? FirstViewController {
            firstViewController.delegate = self
        }
    }

}
```

Finally, in the first View Controller, override the **`prepare(for:sender:)`**
method and pass the second View Controller as the delegate:

```swift
override func prepare(for segue: UIStoryboardSegue, sender: Any?) {
    if let secondViewController = segue.destination as? SecondViewController {
        delegate = secondViewController
    }
}
```

This way, when the button is tapped, the **`didEnterText`** method will be
called on the second View Controller and the label will be updated with the text
entered in the text field.

This task demonstrates an understanding of the Delegation design pattern by
passing data between two View Controllers without tightly coupling them
together.

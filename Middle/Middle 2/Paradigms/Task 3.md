# Task 3

Task:

Write a simple iOS app that demonstrates the use of FRP principles to handle
user input and update the UI accordingly. The app should have a text input field
and a label that displays the number of characters in the input field. The label
should update in real time as the user types, without requiring a button or
other action to trigger the update.

Solution:

First, create a new project in Xcode and add a text field and a label to the
main view controller. In the view controller's **`viewDidLoad()`** method, set
up the text field to emit a stream of its text values using Combine:

```swift
import Combine

class ViewController: UIViewController {

    @IBOutlet weak var textField: UITextField!
    @IBOutlet weak var characterCountLabel: UILabel!

    private var subscriptions = Set<AnyCancellable>()

    override func viewDidLoad() {
        super.viewDidLoad()

        textField.publisher(for: .editingChanged)
            .map { $0.text ?? "" }
            .map { $0.count }
            .map { "\($0) characters" }
            .assign(to: \.text, on: characterCountLabel)
            .store(in: &subscriptions)
    }
}
```

This code sets up a Combine subscription that listens for the
**`editingChanged`** event on the text field, maps the text value to its
character count, formats the count as a string, and assigns the string to the
label's **`text`** property. The **`assign(to:on:)`** method performs the
assignment and returns a subscription, which we store in the **`subscriptions`**
set to keep it alive for as long as the view controller exists.

With this code in place, the label will update in real time as the user types in
the text field, demonstrating the use of FRP principles to handle user input and
update the UI. To further demonstrate FRP principles, you could also add error
handling, debouncing, or other operators to the Combine pipeline.

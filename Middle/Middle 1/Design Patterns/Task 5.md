# Task 5

Task: Implement a basic mediator pattern in an iOS app that has a view
controller and a text field. The view controller should act as a mediator
between the text field and any other parts of the app that need to know about
changes to the text field's text.

Solution:

```swift
// Mediator Protocol
protocol Mediator: AnyObject {
    func textDidChange(text: String)
}

// Mediator Implementation
class ViewController: UIViewController, UITextFieldDelegate, Mediator {
    var textField: UITextField = {
        let textField = UITextField(frame: .zero)
        textField.borderStyle = .roundedRect
        return textField
    }()

    override func viewDidLoad() {
        super.viewDidLoad()

        view.addSubview(textField)
        textField.delegate = self
        textField.translatesAutoresizingMaskIntoConstraints = false
        NSLayoutConstraint.activate([
            textField.centerXAnchor.constraint(equalTo: view.centerXAnchor),
            textField.centerYAnchor.constraint(equalTo: view.centerYAnchor),
            textField.widthAnchor.constraint(equalToConstant: 200)
        ])
    }

    func textDidChange(text: String) {
        // Handle text changes
        print("Text did change: \(text)")
    }

    // MARK: UITextFieldDelegate

    func textField(_ textField: UITextField, shouldChangeCharactersIn range: NSRange, replacementString string: String) -> Bool {
        let updatedText = (textField.text as NSString?)?.replacingCharacters(in: range, with: string) ?? ""
        (UIApplication.shared.delegate as? AppDelegate)?.mediator?.textDidChange(text: updatedText)
        return true
    }
}

// App Delegate
@UIApplicationMain
class AppDelegate: UIResponder, UIApplicationDelegate {
    var mediator: Mediator?
    var window: UIWindow?
    var viewController: ViewController?

    func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
        window = UIWindow(frame: UIScreen.main.bounds)
        viewController = ViewController()
        window?.rootViewController = viewController
        window?.makeKeyAndVisible()

        mediator = viewController

        return true
    }
}
```

In this solution, the **`ViewController`** acts as a mediator between the text
field and any other parts of the app that need to know about changes to the text
field's text. The **`Mediator`** protocol defines the interface that the
mediator will implement. The **`textDidChange(text:)`** method is called by the
text field whenever its text changes.

The **`ViewController`** conforms to the **`Mediator`** protocol and implements
the **`textDidChange(text:)`** method. It also sets itself as the delegate of
the text field and implements the
**`textField(_:shouldChangeCharactersIn:replacementString:)`** method, which is
called by the text field whenever the user types a character. In this method,
the updated text is passed to the mediator via the app delegate's **`mediator`**
property.

The app delegate sets up the window and view controller and creates an instance
of the **`ViewController`**. It also sets the **`mediator`** property to the
view controller so that it can receive notifications of text changes.

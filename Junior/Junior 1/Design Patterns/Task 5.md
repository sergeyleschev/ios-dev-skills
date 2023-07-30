# Task 5

Task:

Create a simple app with a "Login" button on the main screen. When the button is
tapped, a new screen should appear with a "Username" and "Password" text field
and a "Submit" button. When the "Submit" button is tapped, the entered username
and password should be validated. If the validation is successful, the user
should be taken back to the main screen and a message saying "Welcome
<username>!" should be displayed. If the validation fails, an error message
should be displayed on the same screen.

Solution:

1. First, create a protocol called **`LoginDelegate`** with the following
   method:

```swift
protocol LoginDelegate: AnyObject {
    func loginDidSucceed(withUsername username: String)
    func loginDidFail()
}
```

2. Next, create a **`LoginViewController`** with two text fields for the
   username and password and a "Submit" button. When the "Submit" button is
   tapped, validate the entered username and password and call the appropriate
   delegate method.

```swift
class LoginViewController: UIViewController {

    weak var delegate: LoginDelegate?

    // Add username and password text fields here

    func submitButtonTapped() {
        // Validate the entered username and password
        if /* Validation succeeds */ {
            delegate?.loginDidSucceed(withUsername: /* Entered username */)
            dismiss(animated: true, completion: nil)
        } else {
            // Show error message
        }
    }
}
```

3. In the main view controller, implement the **`LoginDelegate`** protocol and
   present the **`LoginViewController`** when the "Login" button is tapped.

```swift
class MainViewController: UIViewController, LoginDelegate {

    func loginButtonTapped() {
        let loginViewController = LoginViewController()
        loginViewController.delegate = self
        present(loginViewController, animated: true, completion: nil)
    }

    func loginDidSucceed(withUsername username: String) {
        // Show welcome message
    }

    func loginDidFail() {
        // Show error message
    }
}

```

That's it! This solution uses the delegation pattern to communicate between the
**`LoginViewController`** and the **`MainViewController`**. When the login
succeeds, the **`LoginViewController`** calls the **`loginDidSucceed`** method
on its delegate (which is the **`MainViewController`**) and dismisses itself.
When the login fails, the **`LoginViewController`** shows an error message on
the same screen.

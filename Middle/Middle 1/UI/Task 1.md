# Task 1

Task: Create a login screen programmatically using autolayout constraints in
code. The screen should contain a logo image view, email and password text
fields, a login button, and a forgot password button. The logo image view should
be centered horizontally on the screen and placed 50 points from the top of the
screen. The email and password text fields should be placed below the logo image
view with a 20 point spacing between them and 30 points from the left and right
edges of the screen. The login button should be centered horizontally below the
text fields with a 20 point spacing from them. The forgot password button should
be placed below the login button with a 20 point spacing and centered
horizontally on the screen.

Solution:

```swift
import UIKit

class LoginViewController: UIViewController {

    override func viewDidLoad() {
        super.viewDidLoad()

        view.backgroundColor = .white

        // Logo ImageView
        let logoImageView = UIImageView(image: UIImage(named: "logo"))
        logoImageView.translatesAutoresizingMaskIntoConstraints = false
        view.addSubview(logoImageView)

        // Email TextField
        let emailTextField = UITextField()
        emailTextField.translatesAutoresizingMaskIntoConstraints = false
        emailTextField.placeholder = "Email"
        emailTextField.borderStyle = .roundedRect
        view.addSubview(emailTextField)

        // Password TextField
        let passwordTextField = UITextField()
        passwordTextField.translatesAutoresizingMaskIntoConstraints = false
        passwordTextField.placeholder = "Password"
        passwordTextField.borderStyle = .roundedRect
        view.addSubview(passwordTextField)

        // Login Button
        let loginButton = UIButton(type: .system)
        loginButton.translatesAutoresizingMaskIntoConstraints = false
        loginButton.setTitle("Login", for: .normal)
        loginButton.titleLabel?.font = UIFont.boldSystemFont(ofSize: 16)
        loginButton.backgroundColor = .blue
        loginButton.setTitleColor(.white, for: .normal)
        loginButton.layer.cornerRadius = 5
        view.addSubview(loginButton)

        // Forgot Password Button
        let forgotPasswordButton = UIButton(type: .system)
        forgotPasswordButton.translatesAutoresizingMaskIntoConstraints = false
        forgotPasswordButton.setTitle("Forgot Password?", for: .normal)
        forgotPasswordButton.setTitleColor(.blue, for: .normal)
        view.addSubview(forgotPasswordButton)

        // Add Constraints
        NSLayoutConstraint.activate([
            // Logo ImageView Constraints
            logoImageView.centerXAnchor.constraint(equalTo: view.centerXAnchor),
            logoImageView.topAnchor.constraint(equalTo: view.topAnchor, constant: 50),

            // Email TextField Constraints
            emailTextField.topAnchor.constraint(equalTo: logoImageView.bottomAnchor, constant: 20),
            emailTextField.leadingAnchor.constraint(equalTo: view.leadingAnchor, constant: 30),
            emailTextField.trailingAnchor.constraint(equalTo: view.trailingAnchor, constant: -30),

            // Password TextField Constraints
            passwordTextField.topAnchor.constraint(equalTo: emailTextField.bottomAnchor, constant: 20),
            passwordTextField.leadingAnchor.constraint(equalTo: view.leadingAnchor, constant: 30),
            passwordTextField.trailingAnchor.constraint(equalTo: view.trailingAnchor, constant: -30),

            // Login Button Constraints
            loginButton.topAnchor.constraint(equalTo: passwordTextField.bottomAnchor, constant: 20),
            loginButton.centerXAnchor.constraint(equalTo: view.centerXAnchor),
            loginButton.widthAnchor.constraint(equalToConstant: 200),

            // Forgot Password Button Constraints
            forgotPasswordButton.topAnchor.constraint(equalTo: loginButton.bottomAnchor, constant: 20),
            forgotPasswordButton.centerXAnchor.constraint(equalTo: view.centerXAnchor)
        ])
    }
}
```

Differences from Junior 3:

-   The developer is now able to create UI programmatically using autolayout
    constraints in code instead of relying solely on Interface Builder or
    Storyboard.
-   The developer is able to use the **`NSLayoutConstraint`** class to create
    and activate constraints between UI elements.
-   The developer understands how to use
    **`translatesAutoresizingMaskIntoConstraints`** property to ensure that the
    constraints are applied

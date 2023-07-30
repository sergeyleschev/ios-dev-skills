# Task 4

Task: Create a simple login screen with two text fields (for email and
password), a "Login" button, and a label for displaying validation errors. Use
auto-layout code to position the UI elements correctly on different screen
sizes. When the "Login" button is tapped, validate the inputs and display any
errors in the label. If the inputs are valid, print them to the console.

Solution:

```swift
import UIKit

class LoginViewController: UIViewController {

    let emailTextField: UITextField = {
        let textField = UITextField()
        textField.placeholder = "Email"
        textField.borderStyle = .roundedRect
        textField.translatesAutoresizingMaskIntoConstraints = false
        return textField
    }()

    let passwordTextField: UITextField = {
        let textField = UITextField()
        textField.placeholder = "Password"
        textField.borderStyle = .roundedRect
        textField.isSecureTextEntry = true
        textField.translatesAutoresizingMaskIntoConstraints = false
        return textField
    }()

    let loginButton: UIButton = {
        let button = UIButton(type: .system)
        button.setTitle("Login", for: .normal)
        button.translatesAutoresizingMaskIntoConstraints = false
        return button
    }()

    let errorLabel: UILabel = {
        let label = UILabel()
        label.textColor = .red
        label.translatesAutoresizingMaskIntoConstraints = false
        return label
    }()

    override func viewDidLoad() {
        super.viewDidLoad()
        view.backgroundColor = .white

        view.addSubview(emailTextField)
        view.addSubview(passwordTextField)
        view.addSubview(loginButton)
        view.addSubview(errorLabel)

        NSLayoutConstraint.activate([
            emailTextField.centerXAnchor.constraint(equalTo: view.centerXAnchor),
            emailTextField.centerYAnchor.constraint(equalTo: view.centerYAnchor, constant: -50),
            emailTextField.widthAnchor.constraint(equalToConstant: 250),

            passwordTextField.centerXAnchor.constraint(equalTo: view.centerXAnchor),
            passwordTextField.topAnchor.constraint(equalTo: emailTextField.bottomAnchor, constant: 20),
            passwordTextField.widthAnchor.constraint(equalToConstant: 250),

            loginButton.centerXAnchor.constraint(equalTo: view.centerXAnchor),
            loginButton.topAnchor.constraint(equalTo: passwordTextField.bottomAnchor, constant: 20),
            loginButton.widthAnchor.constraint(equalToConstant: 100),

            errorLabel.centerXAnchor.constraint(equalTo: view.centerXAnchor),
            errorLabel.topAnchor.constraint(equalTo: loginButton.bottomAnchor, constant: 20)
        ])

        loginButton.addTarget(self, action: #selector(loginButtonTapped), for: .touchUpInside)
    }

    @objc func loginButtonTapped() {
        errorLabel.text = nil

        guard let email = emailTextField.text, !email.isEmpty else {
            errorLabel.text = "Email is required."
            return
        }

        guard let password = passwordTextField.text, !password.isEmpty else {
            errorLabel.text = "Password is required."
            return
        }

        print("Email: \(email), Password: \(password)")
    }
}

```

Differences from Middle level 1:

-   The solution uses auto-layout code instead of storyboard to position the UI
    elements.
-   The solution uses target-action pattern instead of delegation pattern to
    handle button tap events.
-   The solution validates the input fields and displays error messages if
    needed, instead of assuming the inputs are always valid.

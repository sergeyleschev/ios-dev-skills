# Task 2

Task: Implement a simple login form using ReactiveSwift.

Solution:

```swift
import UIKit
import ReactiveSwift
import ReactiveCocoa

class LoginViewController: UIViewController {

    // MARK: - Outlets
    @IBOutlet weak var usernameTextField: UITextField!
    @IBOutlet weak var passwordTextField: UITextField!
    @IBOutlet weak var loginButton: UIButton!

    // MARK: - Properties
    private let viewModel = LoginViewModel()
    private let disposeBag = CompositeDisposable()

    // MARK: - View Lifecycle
    override func viewDidLoad() {
        super.viewDidLoad()

        // Bind the text fields to the view model
        usernameTextField.reactive.text <~ viewModel.username
        passwordTextField.reactive.text <~ viewModel.password

        // Bind the login button to the view model
        loginButton.reactive.isEnabled <~ viewModel.isLoginButtonEnabled

        // Subscribe to the login button's signal
        loginButton.reactive.controlEvents(.touchUpInside).observeValues { [weak self] _ in
            self?.viewModel.login()
        }
    }

    // MARK: - Deinitialization
    deinit {
        disposeBag.dispose()
    }

}

class LoginViewModel {

    // MARK: - Properties
    let username = MutableProperty<String>("")
    let password = MutableProperty<String>("")
    let isLoginButtonEnabled: Property<Bool>

    // MARK: - Initializer
    init() {
        // Combine the username and password properties to create the login button enabled property
        isLoginButtonEnabled = Property.combineLatest(username, password).map { !$0.0.isEmpty && !$0.1.isEmpty }
    }

    // MARK: - Public Methods
    func login() {
        // Perform login logic here
    }
}
```

Differences from Junior 3:

-   Uses ReactiveSwift, a reactive programming framework.
-   Introduces the use of **`MutableProperty`**, a mutable value in
    ReactiveSwift.
-   Utilizes **`Property.combineLatest`** to combine the **`username`** and
    **`password`** properties into a single **`isLoginButtonEnabled`** property.
-   Observes values from the **`loginButton`** using ReactiveSwift's
    **`reactive.controlEvents`**.

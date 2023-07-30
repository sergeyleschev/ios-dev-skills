# Task 3

Task: Implement a simple login screen using FRP principles. The screen should
have two text fields for the user to enter their email and password, and a login
button that is enabled only when both fields have text. Upon tapping the login
button, the app should simulate a network call that either succeeds or fails
with a random delay between 1-3 seconds. Display an alert to the user with the
appropriate message indicating success or failure.

Solution:

```swift
import UIKit
import RxSwift
import RxCocoa

class LoginViewController: UIViewController {

    @IBOutlet weak var emailTextField: UITextField!
    @IBOutlet weak var passwordTextField: UITextField!
    @IBOutlet weak var loginButton: UIButton!

    let disposeBag = DisposeBag()

    override func viewDidLoad() {
        super.viewDidLoad()

        let emailObservable = emailTextField.rx.text.orEmpty
        let passwordObservable = passwordTextField.rx.text.orEmpty

        let isFormValidObservable = Observable.combineLatest(emailObservable, passwordObservable)
            .map { email, password in
                !email.isEmpty && !password.isEmpty
            }

        isFormValidObservable
            .bind(to: loginButton.rx.isEnabled)
            .disposed(by: disposeBag)

        loginButton.rx.tap
            .flatMapLatest { [weak self] _ -> Observable<Bool> in
                guard let self = self else { return Observable.just(false) }
                return self.login()
            }
            .subscribe(onNext: { [weak self] isSuccess in
                guard let self = self else { return }
                let message = isSuccess ? "Login successful" : "Login failed"
                let alert = UIAlertController(title: "Result", message: message, preferredStyle: .alert)
                alert.addAction(UIAlertAction(title: "OK", style: .default, handler: nil))
                self.present(alert, animated: true, completion: nil)
            })
            .disposed(by: disposeBag)
    }

    func login() -> Observable<Bool> {
        let isSuccess = arc4random_uniform(2) == 1
        let delay = arc4random_uniform(3) + 1
        return Observable.just(isSuccess)
            .delay(.seconds(Int(delay)), scheduler: MainScheduler.instance)
    }
}

```

Differences from Junior 3 level:

-   The task involves using FRP principles and RxSwift library, which requires
    understanding of observables, operators, and subscriptions.
-   The task involves simulating a network call and displaying the result to the
    user using an alert controller.
-   The solution uses a **`DisposeBag`** to dispose of subscriptions when the
    view controller is deallocated.
-   The solution uses **`flatMapLatest`** operator to cancel previous login
    requests if a new login request is made.

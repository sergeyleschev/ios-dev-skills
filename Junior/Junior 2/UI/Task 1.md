# Task 1

Task:

Create a basic UI in Interface Builder for an app that displays a form for the
user to enter their personal information. The form should consist of several
text fields, including name, email, and phone number, as well as a submit
button.

Solution:

Step 1: Create a new XIB file called "PersonalInfoViewController" and open it in
Interface Builder.

Step 2: Drag a stack view onto the view and set its constraints so that it fills
the entire view.

Step 3: Add several text fields to the stack view for the user to enter their
personal information, such as name, email, and phone number.

Step 4: Add a submit button to the bottom of the stack view.

Step 5: Set the constraints for the stack view and its subviews so that they are
properly positioned and sized within the view.

Step 6: Create outlets for the text fields and submit button in the
PersonalInfoViewController class.

```swift
@IBOutlet weak var nameTextField: UITextField!
@IBOutlet weak var emailTextField: UITextField!
@IBOutlet weak var phoneTextField: UITextField!
@IBOutlet weak var submitButton: UIButton!
```

Step 7: In the viewDidLoad method of the PersonalInfoViewController class, add a
target to the submit button so that it calls a method when it is tapped.

```swift
override func viewDidLoad() {
    super.viewDidLoad()

    submitButton.addTarget(self, action: #selector(submitButtonTapped), for: .touchUpInside)
}
```

Step 8: Implement the submitButtonTapped method to validate the user's input and
save their personal information.

```swift
@objc private func submitButtonTapped() {
    // validate user input and save personal information
}
```

Differences from Junior Level 1:

This task is slightly more complex than the previous one, as it involves
creating a form with multiple text fields and a submit button. Additionally, it
requires adding a target to the submit button to handle user input, which is a
new concept for a Junior Level 1 developer. Finally, this task requires
implementing some basic input validation, which is an important skill for any
iOS developer to have.

# Task 3

Task: Implement a subclass of UIViewController called "CustomViewController".
This subclass should have a property called "data" of type [String: Any], which
can be used to pass data to the view controller. The view controller should also
have a method called "configureView" that configures the UI based on the data
passed in.

Solution:

```swift
class CustomViewController: UIViewController {
    var data: [String: Any]?

    override func viewDidLoad() {
        super.viewDidLoad()
        configureView()
    }

    func configureView() {
        guard let data = data else { return }
        // configure UI based on data
        if let title = data["title"] as? String {
            self.title = title
        }
        if let backgroundColor = data["backgroundColor"] as? UIColor {
            view.backgroundColor = backgroundColor
        }
        // configure other UI elements based on data
    }
}
```

Differences from Junior 2 level:

-   Introduces the concept of subclassing a built-in iOS class
    (UIViewController)
-   Introduces the concept of creating a custom property and using it to pass
    data to the view controller
-   Introduces the concept of creating a custom method (configureView) to
    configure the UI based on the passed data

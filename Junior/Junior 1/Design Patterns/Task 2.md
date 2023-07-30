# Task 2

Task: Create a simple app that uses Target-Action to change the background color
of a View Controller when a button is tapped.

Solution:

First, create a new Xcode project and add a View Controller to the storyboard.
Then, add a button to the View Controller and set its title to "Change Color."

Next, create a new Swift file called **`ViewController.swift`** and create a
subclass of **`UIViewController`** called **`ViewController`**. In the
**`ViewController`** class, add a property called **`backgroundColor`** to keep
track of the current background color:

```swift
class ViewController: UIViewController {
    var backgroundColor: UIColor = .white
}
```

Then, override the **`viewDidLoad`** method to set the initial background color
of the View Controller:

```swift
override func viewDidLoad() {
    super.viewDidLoad()
    view.backgroundColor = backgroundColor
}
```

In the storyboard, connect the button to an **`IBAction`** method in the
**`ViewController`** class:

```swift
@IBAction func buttonTapped(_ sender: UIButton) {

}
```

Next, create a new Swift file called **`ButtonDelegate.swift`** and create a
protocol called **`ButtonDelegate`** that defines a method to change the
background color:

```swift
protocol ButtonDelegate {
    func changeBackgroundColor()
}
```

In the **`ViewController`** class, add a property called **`delegate`** of type
**`ButtonDelegate`**:

```swift
var delegate: ButtonDelegate?
```

In the **`buttonTapped`** method, call the **`changeBackgroundColor`** method on
the delegate:

```swift
@IBAction func buttonTapped(_ sender: UIButton) {
    delegate?.changeBackgroundColor()
}
```

In the **`AppDelegate`** class, implement the **`ButtonDelegate`** protocol by
changing the background color of the View Controller:

```swift
class AppDelegate: UIResponder, UIApplicationDelegate, ButtonDelegate {

    var window: UIWindow?
    var viewController: ViewController?

    func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {
        viewController = window?.rootViewController as? ViewController
        viewController?.delegate = self
        return true
    }

    func changeBackgroundColor() {
        guard let viewController = viewController else { return }
        let newColor = UIColor(red: .random(in: 0...1), green: .random(in: 0...1), blue: .random(in: 0...1), alpha: 1.0)
        viewController.backgroundColor = newColor
        viewController.view.backgroundColor = newColor
    }

}
```

In the **`didFinishLaunchingWithOptions`** method, set the **`delegate`**
property of the View Controller to **`self`** (the **`AppDelegate`**).

Now, when the button is tapped, the **`changeBackgroundColor`** method on the
**`AppDelegate`** will be called, and the background color of the View
Controller will change to a random color.

This task demonstrates an understanding of the Target-Action design pattern by
connecting a button to a method using a protocol and delegate pattern. It also
demonstrates the use of the MVC design pattern by separating the logic for
changing the background color into a separate class (**`AppDelegate`**).

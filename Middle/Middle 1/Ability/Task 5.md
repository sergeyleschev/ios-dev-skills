# Task 5

Task: Create a custom tab bar controller that includes a badge indicator on one
of the tabs, indicating the number of unread messages.

Solution:

```swift
class CustomTabBarController: UITabBarController {

    override func viewDidLoad() {
        super.viewDidLoad()

        // Create and configure the view controllers for each tab
        let firstViewController = UIViewController()
        let secondViewController = UIViewController()
        let thirdViewController = UIViewController()

        firstViewController.tabBarItem = UITabBarItem(tabBarSystemItem: .favorites, tag: 0)
        secondViewController.tabBarItem = UITabBarItem(tabBarSystemItem: .history, tag: 1)
        thirdViewController.tabBarItem = UITabBarItem(tabBarSystemItem: .downloads, tag: 2)

        // Add a badge indicator to the third tab
        thirdViewController.tabBarItem.badgeValue = "3"

        // Set the view controllers for the tab bar controller
        self.viewControllers = [firstViewController, secondViewController, thirdViewController]
    }
}
```

Differences from Junior 3 level:

-   Creating a custom tab bar controller
-   Configuring and adding tab bar items
-   Adding a badge indicator to a tab bar item

# Task 2

Task: Create a custom tab bar controller with a centered button that triggers a
modal view. The tab bar controller should have a custom background color and
font for the tab bar items. The modal view should have a custom presentation
animation.

Solution:

```swift
import UIKit

class CustomTabBarController: UITabBarController {

    override func viewDidLoad() {
        super.viewDidLoad()

        // Set custom background color for tab bar
        tabBar.barTintColor = UIColor(red: 0.8, green: 0.9, blue: 1.0, alpha: 1.0)

        // Set custom font for tab bar items
        let fontAttributes = [NSAttributedString.Key.font: UIFont.systemFont(ofSize: 18)]
        UITabBarItem.appearance().setTitleTextAttributes(fontAttributes, for: .normal)

        // Add centered button
        let button = UIButton(type: .custom)
        button.setBackgroundImage(UIImage(named: "button-icon"), for: .normal)
        button.addTarget(self, action: #selector(buttonTapped), for: .touchUpInside)
        view.addSubview(button)

        button.translatesAutoresizingMaskIntoConstraints = false
        NSLayoutConstraint.activate([
            button.centerXAnchor.constraint(equalTo: tabBar.centerXAnchor),
            button.topAnchor.constraint(equalTo: tabBar.topAnchor, constant: -32),
            button.widthAnchor.constraint(equalToConstant: 64),
            button.heightAnchor.constraint(equalToConstant: 64)
        ])
    }

    @objc func buttonTapped() {
        // Present modal view controller
        let modalVC = ModalViewController()
        modalVC.modalPresentationStyle = .custom
        modalVC.transitioningDelegate = self
        present(modalVC, animated: true, completion: nil)
    }

}

class ModalViewController: UIViewController, UIViewControllerTransitioningDelegate {

    override func viewDidLoad() {
        super.viewDidLoad()

        view.backgroundColor = .white
    }

    override func viewDidAppear(_ animated: Bool) {
        super.viewDidAppear(animated)

        // Custom presentation animation
        view.transform = CGAffineTransform(scaleX: 0.1, y: 0.1)
        UIView.animate(withDuration: 0.5, delay: 0, usingSpringWithDamping: 0.5, initialSpringVelocity: 0.5, options: [], animations: {
            self.view.transform = .identity
        }, completion: nil)
    }

    func presentationController(forPresented presented: UIViewController, presenting: UIViewController?, source: UIViewController) -> UIPresentationController? {
        return CustomPresentationController(presentedViewController: presented, presenting: presenting)
    }

}

class CustomPresentationController: UIPresentationController {

    override var frameOfPresentedViewInContainerView: CGRect {
        let size = CGSize(width: containerView!.frame.width * 0.8, height: containerView!.frame.height * 0.5)
        return CGRect(origin: CGPoint(x: containerView!.center.x - size.width/2, y: containerView!.center.y - size.height/2), size: size)
    }

    override func presentationTransitionWillBegin() {
        containerView?.addSubview(presentedView!)
    }

}
```

Differences from Middle level 2:

-   The solution creates a custom tab bar controller, instead of using the
    default **`UITabBarController`**.
-   The solution adds a centered button that triggers a modal view, instead of
    using the default tab bar items.
-   The solution uses a custom presentation animation for the modal view.
-   The solution uses a custom **`UIPresentationController`** to define the
    frame of the presented view.

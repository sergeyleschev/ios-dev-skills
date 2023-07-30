# Task 1

Task:

Create a simple shopping cart application that allows users to add and remove
items from the cart. Use the delegate design pattern to notify the view
controller when the cart is updated.

Solution:

First, create a protocol called ShoppingCartDelegate:

```swift
protocol ShoppingCartDelegate: AnyObject {
    func cartDidUpdate()
}
```

Next, create a ShoppingCart class that will manage the items in the cart:

```swift
class ShoppingCart {
    var items: [String] = []
    weak var delegate: ShoppingCartDelegate?

    func addItem(_ item: String) {
        items.append(item)
        delegate?.cartDidUpdate()
    }

    func removeItem(_ item: String) {
        if let index = items.firstIndex(of: item) {
            items.remove(at: index)
            delegate?.cartDidUpdate()
        }
    }
}
```

In the view controller, implement the ShoppingCartDelegate protocol and set the
view controller as the delegate of the shopping cart:

```swift
class ViewController: UIViewController, ShoppingCartDelegate {
    let shoppingCart = ShoppingCart()

    override func viewDidLoad() {
        super.viewDidLoad()
        shoppingCart.delegate = self
    }

    func cartDidUpdate() {
        // Update UI to reflect changes in the cart
    }

    // Add or remove items from the cart as needed
}
```

The key difference between this task and the previous one is that it requires
the use of the delegate design pattern. By using delegates, the view controller
can be notified when the cart is updated without having to constantly poll the
shopping cart object. This leads to cleaner, more efficient code. Additionally,
this task requires the use of protocols, which is a key concept in Swift and iOS
development.

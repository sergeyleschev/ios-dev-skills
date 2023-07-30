# Task 5

Task: Implement a mediator pattern to communicate between two view controllers,
A and B.

Solution:

1. Create a mediator class that will handle the communication between the view
   controllers. This class should have a reference to both view controllers.

```swift
class Mediator {

    private weak var viewControllerA: ViewControllerA?
    private weak var viewControllerB: ViewControllerB?

    init(viewControllerA: ViewControllerA, viewControllerB: ViewControllerB) {
        self.viewControllerA = viewControllerA
        self.viewControllerB = viewControllerB
    }

    // Methods to handle communication between the view controllers

}
```

2. Add methods to the mediator class that will be called from one view
   controller to send data to the other view controller.

```swift
extension Mediator {

    func sendDataFromA(toB data: Any) {
        viewControllerB?.handleDataFromA(data)
    }

    func sendDataFromB(toA data: Any) {
        viewControllerA?.handleDataFromB(data)
    }

}
```

3. In both view controllers, create a reference to the mediator and pass it to
   the other view controller during initialization.

```swift
class ViewControllerA: UIViewController {

    var mediator: Mediator?

    override func viewDidLoad() {
        super.viewDidLoad()

        let viewControllerB = ViewControllerB()
        mediator = Mediator(viewControllerA: self, viewControllerB: viewControllerB)
        viewControllerB.mediator = mediator

    }

    func sendDataToB(data: Any) {
        mediator?.sendDataFromA(toB: data)
    }

    func handleDataFromB(_ data: Any) {
        // Handle the data received from view controller B
    }

}

class ViewControllerB: UIViewController {

    var mediator: Mediator?

    override func viewDidLoad() {
        super.viewDidLoad()

        let viewControllerA = ViewControllerA()
        mediator = Mediator(viewControllerA: viewControllerA, viewControllerB: self)
        viewControllerA.mediator = mediator

    }

    func sendDataToA(data: Any) {
        mediator?.sendDataFromB(toA: data)
    }

    func handleDataFromA(_ data: Any) {
        // Handle the data received from view controller A
    }

}
```

In this solution, we have created a mediator class that handles the
communication between the two view controllers. Each view controller has a
reference to the mediator, and can use it to send data to the other view
controller.

Differences that indicate the development of the developer to the level of
middle 2 from the level of middle 1:

-   Understanding of the mediator pattern and its use cases.
-   Ability to create a mediator class that can handle communication between
    multiple objects.
-   Ability to pass references between objects to enable communication through
    the mediator.
-   Understanding of the weak reference and how to use it to avoid retain
    cycles.

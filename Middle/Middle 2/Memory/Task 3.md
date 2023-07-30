# Task 3

Task: Given a view controller that creates and retains a large data model
object, refactor the view controller to use a weak reference to the data model
object to prevent memory leaks.

Solution:

```swift
class MyViewController: UIViewController {
    weak var dataModel: MyDataModel?

    override func viewDidLoad() {
        super.viewDidLoad()

        dataModel = MyDataModel()
        // use the dataModel object
    }

    // other methods
}

class MyDataModel {
    // implementation of the data model
}
```

In this solution, we create a weak reference to the **`MyDataModel`** object in
the **`MyViewController`** class. This ensures that the **`MyDataModel`** object
is deallocated when there are no strong references to it, thus preventing memory
leaks. The weak reference is declared using the **`weak`** keyword before the
variable declaration. The **`viewDidLoad()`** method instantiates the
**`MyDataModel`** object and assigns it to the **`dataModel`** variable. The
**`MyDataModel`** object can be used as usual, but now with the added benefit of
not causing a memory leak.

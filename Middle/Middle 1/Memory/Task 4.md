# Task 4

Task: Given a UIViewController that presents a child UIViewController and also
stores a reference to it. How would you ensure that the child view controller
gets deallocated properly when the parent view controller is dismissed?

Solution: To ensure that the child view controller is deallocated properly when
the parent view controller is dismissed, we need to make sure to break the
retain cycle between the two view controllers.

One way to do this is by setting the reference to the child view controller to
**`nil`** when the parent view controller is dismissed. We can do this by
implementing the **`viewWillDisappear`** method in the parent view controller
and setting the reference to the child view controller to **`nil`** inside it.

Alternatively, we can use an **`unowned`** or **`weak`** reference for the
parent view controller inside the child view controller. This will ensure that
the child view controller does not hold a strong reference to the parent view
controller, and the parent view controller can be deallocated properly. We can
use either of these keywords depending on the specific use case and whether we
want the child view controller to be automatically deallocated when the parent
view controller is deallocated.

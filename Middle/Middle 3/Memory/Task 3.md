# Task 3

Task:

You have a custom UIView subclass that includes several subviews. You notice
that when the view is removed from the superview, there are still some strong
references to it that are not getting released, leading to a memory leak.
Identify and fix the issue.

Solution:

The issue is likely due to the strong reference cycle created between the custom
view and its subviews. To fix this, we can make use of weak references.

First, we need to identify any strong references to the custom view or its
subviews within the view hierarchy. This could be due to any strong references
created within the custom view's code or in any external code that uses the
custom view.

Once we have identified any strong references, we can break the strong reference
cycle by changing the reference to a weak reference. For example, if the custom
view holds a strong reference to one of its subviews, we can change it to a weak
reference instead:

```swift
weak var subview: UIView?
```

We can also use unowned references if we are certain that the referenced object
will not be nil.

By using weak or unowned references appropriately, we can ensure that the memory
is properly managed and there are no memory leaks.

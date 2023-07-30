# Task 3

Task:

Given a view hierarchy with complex auto layout constraints, create a method
that takes layout and diff calculation to a non-main thread, while ensuring that
the UI is still updated on the main thread.

Solution:

1. Create a private serial queue:

```swift
private let layoutQueue = DispatchQueue(label: "com.example.layout", qos: .userInitiated)
```

2. Inside your view controller, create a method that performs the layout and
   diff calculation on the layoutQueue:

```swift
private func updateLayout() {
    layoutQueue.async { [weak self] in
        // Perform layout and diff calculation
        // ...

        DispatchQueue.main.async {
            // Update UI on main thread
            self?.view.setNeedsLayout()
            self?.view.layoutIfNeeded()
        }
    }
}
```

3. Call the **`updateLayout`** method whenever you need to update the layout,
   such as in **`viewDidLoad`**, **`viewWillAppear`**, and whenever the data
   changes.

Differences from Senior 1 level:

-   The developer understands the importance of performance and is able to
    optimize the layout and diff calculation by moving it to a background
    thread.
-   The developer knows how to ensure that the UI is still updated on the main
    thread to avoid crashes and synchronization issues.

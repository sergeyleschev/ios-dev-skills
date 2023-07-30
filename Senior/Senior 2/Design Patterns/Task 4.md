# Task 4

Task: Implement a simple example of the Observer pattern using
NotificationCenter. Create a class that will act as the observer and another
class that will act as the subject. When a specific event happens on the
subject, it should notify the observer using NotificationCenter.

Solution:

```swift
// Observer class
class MyObserver {
    init() {
        NotificationCenter.default.addObserver(self, selector: #selector(handleNotification), name: Notification.Name("MyNotification"), object: nil)
    }

    deinit {
        NotificationCenter.default.removeObserver(self)
    }

    @objc func handleNotification() {
        print("Received notification")
    }
}

// Subject class
class MySubject {
    func doSomething() {
        // Do some work...
        // Notify observers
        NotificationCenter.default.post(name: Notification.Name("MyNotification"), object: nil)
    }
}

// Usage
let observer = MyObserver()
let subject = MySubject()

subject.doSomething() // Observer should receive notification
```

Differences between Senior 1 and Senior 2:

-   Senior 2 should have a deeper understanding of design patterns beyond just
    knowing the sweet spot between dependency injection and service locator.
    They should be able to apply multiple design patterns together in a single
    solution.
-   Senior 2 should be able to identify and solve more complex problems and
    challenges in a more efficient manner.
-   Senior 2 should have better communication and collaboration skills, and be
    able to lead and mentor junior team members.

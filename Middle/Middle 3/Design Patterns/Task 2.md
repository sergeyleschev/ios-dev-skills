# Task 2

Task: Implement Observer Pattern

Write a simple implementation of the Observer pattern using Swift that allows an
object (subject) to notify a group of dependent objects (observers)
automatically of any state changes.

Solution:

```swift
protocol Observer {
    func update()
}

protocol Subject {
    func register(observer: Observer)
    func remove(observer: Observer)
    func notifyObservers()
}

class MySubject: Subject {
    private var observers = [Observer]()
    var state: Int = 0 {
        didSet {
            notifyObservers()
        }
    }

    func register(observer: Observer) {
        observers.append(observer)
    }

    func remove(observer: Observer) {
        if let index = observers.firstIndex(where: { $0 === observer }) {
            observers.remove(at: index)
        }
    }

    func notifyObservers() {
        observers.forEach { $0.update() }
    }
}

class MyObserver: Observer {
    private let subject: MySubject

    init(subject: MySubject) {
        self.subject = subject
        self.subject.register(observer: self)
    }

    func update() {
        print("MyObserver received an update. New state is \(subject.state)")
    }
}

// Usage
let subject = MySubject()
let observer1 = MyObserver(subject: subject)
let observer2 = MyObserver(subject: subject)

subject.state = 1 // Output: MyObserver received an update. New state is 1

subject.remove(observer: observer2)
subject.state = 2 // Output: MyObserver received an update. New state is 2
```

Differences that indicate the development of the developer to the level of
middle 3 from the level of middle 2:

-   Proper use of protocols to define the contracts for the Observer and Subject
    classes, making the code more modular and scalable.
-   Separation of concerns between the Observer and Subject classes, where the
    Subject only handles registration, removal, and notification of observers,
    while the Observer only handles the logic for updating its state based on
    the Subject's state changes.
-   Use of the **`===`** operator to compare object references when removing
    observers from the list, ensuring that the correct observer is removed.
-   Implementation of a simple usage scenario to demonstrate the functionality
    of the Observer pattern.

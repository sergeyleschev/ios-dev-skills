# Task 2

Task: Write a simple implementation of the Observer pattern using the Swift
programming language. Assume that you have a class **`Subject`** that maintains
a list of observers and has methods **`attach(observer: Observer)`**,
**`detach(observer: Observer)`**, and **`notify()`** to manage and notify the
observers. Write the necessary code to allow the observers to receive updates
from the **`Subject`** object.

Solution:

```swift
protocol Observer {
    func update()
}

class Subject {
    private var observers: [Observer] = []

    func attach(observer: Observer) {
        observers.append(observer)
    }

    func detach(observer: Observer) {
        observers.removeAll { $0 === observer }
    }

    func notify() {
        observers.forEach { $0.update() }
    }
}

class ConcreteObserverA: Observer {
    func update() {
        print("Observer A has been notified")
    }
}

class ConcreteObserverB: Observer {
    func update() {
        print("Observer B has been notified")
    }
}

let subject = Subject()
let observerA = ConcreteObserverA()
let observerB = ConcreteObserverB()

subject.attach(observer: observerA)
subject.attach(observer: observerB)

subject.notify()

subject.detach(observer: observerA)

subject.notify()
```

Differences between Senior 1 and Senior 2 developers:

-   A Senior 2 developer has a deep understanding of algorithms and data
    structures and can apply them to solve complex problems.
-   A Senior 2 developer has extensive experience in building and scaling
    distributed systems and understands the intricacies of network programming.
-   A Senior 2 developer is a master of software engineering principles and can
    design and implement highly maintainable and extensible code.
-   A Senior 2 developer has excellent communication skills and can collaborate
    effectively with cross-functional teams.

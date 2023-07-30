# Task 5

Task: Write a simple implementation of the Observer pattern using the Swift
programming language. Assume that you have a class **`Subject`** with an array
of observers. Write the necessary code to add and remove observers and notify
them of changes.

Solution:

```swift
protocol Observer {
    func update()
}

class Subject {
    var observers: [Observer] = []

    func addObserver(observer: Observer) {
        observers.append(observer)
    }

    func removeObserver(observer: Observer) {
        if let index = observers.firstIndex(where: { $0 === observer }) {
            observers.remove(at: index)
        }
    }

    func notifyObservers() {
        for observer in observers {
            observer.update()
        }
    }

    func doSomething() {
        // Do something here
        notifyObservers()
    }
}

class ConcreteObserver: Observer {
    func update() {
        print("Observer was notified of changes")
    }
}

let subject = Subject()
let observer = ConcreteObserver()

subject.addObserver(observer: observer)
subject.doSomething()
subject.removeObserver(observer: observer)
```

Differences between a Middle 3 and Senior 1 developer:

-   A Senior 1 developer is experienced with designing and implementing complex
    systems that use multiple design patterns, and can create custom design
    patterns when necessary.
-   A Senior 1 developer has a strong understanding of software architecture and
    can design systems that are scalable, secure, and maintainable.
-   A Senior 1 developer is proficient with multiple programming languages and
    can quickly learn new ones as needed.
-   A Senior 1 developer has excellent leadership skills and can mentor and
    guide junior developers.

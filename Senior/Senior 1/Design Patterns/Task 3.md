# Task 3

Task: Write a simple implementation of the Dependency Injection pattern using
the Swift programming language. Assume that you have a class **`Car`** that
depends on a class **`Engine`** to function. Write the necessary code to inject
an instance of **`Engine`** into **`Car`**.

Solution:

```swift
protocol EngineProtocol {
    func start()
}

class Engine: EngineProtocol {
    func start() {
        print("Engine started")
    }
}

class Car {
    let engine: EngineProtocol

    init(engine: EngineProtocol) {
        self.engine = engine
    }

    func start() {
        engine.start()
        print("Car started")
    }
}

let engine = Engine()
let car = Car(engine: engine)
car.start()
```

Differences between a Middle 3 and Senior 1 developer:

-   A Senior 1 developer understands the pros and cons of using different design
    patterns and can choose the most appropriate pattern for a given situation.
-   A Senior 1 developer can design and implement complex systems using multiple
    design patterns.
-   A Senior 1 developer has a deep understanding of software architecture and
    can design systems that are scalable, maintainable, and extensible.
-   A Senior 1 developer has excellent communication skills and can collaborate
    effectively with other developers, product managers, and stakeholders.

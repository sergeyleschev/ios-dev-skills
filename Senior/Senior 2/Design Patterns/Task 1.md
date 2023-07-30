# Task 1

Task: Write a simple implementation of the Strategy pattern using the Swift
programming language. Assume that you have a class **`Context`** that takes a
strategy object, which has a method **`execute()`**. Write the necessary code to
allow the **`Context`** class to switch between different strategy objects at
runtime.

Solution:

```swift
protocol Strategy {
    func execute()
}

class Context {
    var strategy: Strategy

    init(strategy: Strategy) {
        self.strategy = strategy
    }

    func executeStrategy() {
        strategy.execute()
    }

    func setStrategy(strategy: Strategy) {
        self.strategy = strategy
    }
}

class ConcreteStrategyA: Strategy {
    func execute() {
        print("Executing strategy A")
    }
}

class ConcreteStrategyB: Strategy {
    func execute() {
        print("Executing strategy B")
    }
}

let context = Context(strategy: ConcreteStrategyA())
context.executeStrategy()
context.setStrategy(strategy: ConcreteStrategyB())
context.executeStrategy()
```

Differences between Senior 1 and Senior 2 developers:

-   A Senior 2 developer has a deeper understanding of software architecture and
    can design and implement highly scalable and performant systems.
-   A Senior 2 developer is an expert in one or more programming languages and
    can write highly efficient code.
-   A Senior 2 developer is a thought leader in their field and can contribute
    to open source projects and speak at conferences.
-   A Senior 2 developer has exceptional leadership skills and can manage and
    mentor large teams of developers. ß

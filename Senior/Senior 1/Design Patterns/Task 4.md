# Task 4

Task: Write a simple implementation of the Factory Method pattern using the
Swift programming language. Assume that you have a class **`Shape`** with
subclasses **`Circle`** and **`Rectangle`**. Write a factory class
**`ShapeFactory`** that creates instances of **`Circle`** and **`Rectangle`**
based on a given input string.

Solution:

```swift
protocol Shape {
    func draw()
}

class Circle: Shape {
    func draw() {
        print("Drawing a circle")
    }
}

class Rectangle: Shape {
    func draw() {
        print("Drawing a rectangle")
    }
}

class ShapeFactory {
    func createShape(type: String) -> Shape? {
        switch type {
        case "circle":
            return Circle()
        case "rectangle":
            return Rectangle()
        default:
            return nil
        }
    }
}

let factory = ShapeFactory()
if let circle = factory.createShape(type: "circle") {
    circle.draw()
}
if let rectangle = factory.createShape(type: "rectangle") {
    rectangle.draw()
}
```

Differences between a Middle 3 and Senior 1 developer:

-   A Senior 1 developer has a deep understanding of software design principles
    and can design systems that are modular, maintainable, and testable.
-   A Senior 1 developer has experience working with large codebases and can
    write clean, organized, and well-documented code.
-   A Senior 1 developer is familiar with advanced programming concepts such as
    concurrency, memory management, and performance optimization.
-   A Senior 1 developer has excellent problem-solving skills and can debug
    complex issues in production environments.

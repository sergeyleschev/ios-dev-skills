# Task 3

Task: Implement a simple class called **`Rectangle`** that has properties for
width and height. Add a method called **`area()`** that returns the area of the
rectangle. Instantiate an object of this class with a width of 5 and a height of
10, and print its area.

Solution:

```swift
class Rectangle {
    var width: Double
    var height: Double

    init(width: Double, height: Double) {
        self.width = width
        self.height = height
    }

    func area() -> Double {
        return width * height
    }
}

let rect = Rectangle(width: 5, height: 10)
print("Area of rectangle is \(rect.area())")
```

In this task, the candidate is asked to create a simple class that demonstrates
their understanding of creating classes with properties and methods in an OOP
paradigm. They are also asked to instantiate an object of this class and use its
method to calculate the area of the rectangle. The solution should demonstrate
the candidate's knowledge of creating classes, initializing objects, and
accessing their properties and methods.

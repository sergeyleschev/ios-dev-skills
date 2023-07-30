# Task 4

Task: Create a **`Rectangle`** struct with properties **`width`** and
**`height`**, and a method **`area()`** that calculates the area of the
rectangle. Then create an extension on **`Rectangle`** that adds a method
**`isSquare()`** that returns true if the rectangle is a square (i.e. its width
and height are equal). Finally, create an instance of **`Rectangle`** and call
both the **`area()`** and **`isSquare()`** methods.

Solution:

```swift
struct Rectangle {
    var width: Double
    var height: Double

    func area() -> Double {
        return width * height
    }
}

extension Rectangle {
    func isSquare() -> Bool {
        return width == height
    }
}

let rectangle = Rectangle(width: 5.0, height: 5.0)
print(rectangle.area())
print(rectangle.isSquare())
```

Difference from Junior 1: The Junior 2 developer should be able to create and
use extensions, which is demonstrated by the creation of the extension on
**`Rectangle`** that adds the **`isSquare()`** method. They should also be able
to create and use struct instances with properties and methods, as shown in the
creation of the **`Rectangle`** instance and the calls to the **`area()`** and
**`isSquare()`** methods.

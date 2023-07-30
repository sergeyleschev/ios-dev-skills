# Task 5

Task: Write a function in Swift that demonstrates the use of dynamic dispatch
and how it differs from static dispatch.

Solution:

```swift
class Shape {
    func draw() {
        print("Drawing a shape")
    }
}

class Circle: Shape {
    override func draw() {
        print("Drawing a circle")
    }
}

class Square: Shape {
    override func draw() {
        print("Drawing a square")
    }
}

func drawShapes(shapes: [Shape]) {
    for shape in shapes {
        shape.draw() // dynamic dispatch
    }
}

func drawSquare(square: Square) {
    square.draw() // static dispatch
}

let shapes: [Shape] = [Circle(), Square()]

drawShapes(shapes: shapes) // Output: "Drawing a circle" "Drawing a square"

let square = Square()
drawSquare(square: square) // Output: "Drawing a square"
```

In this example, we have a base **`Shape`** class and two subclasses,
**`Circle`** and **`Square`**. The **`Shape`** class has a **`draw()`** method
that is overridden by each subclass to draw the corresponding shape.

The **`drawShapes()`** function takes an array of **`Shape`** objects and calls
the **`draw()`** method on each one, which uses dynamic dispatch to call the
appropriate **`draw()`** method for each subclass.

The **`drawSquare()`** function takes a **`Square`** object and calls its
**`draw()`** method directly, which uses static dispatch because the object's
type is known at compile-time.

The difference between dynamic and static dispatch is that dynamic dispatch uses
runtime type information to determine which method to call, while static
dispatch uses compile-time type information. Dynamic dispatch allows for more
flexibility and polymorphism in the code, while static dispatch can be more
efficient.

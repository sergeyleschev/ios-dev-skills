# Task 1

Task: Create a class called **`Person`** with properties **`name`**, **`age`**,
and **`gender`**, and a function called **`introduce`** that prints a greeting
with the person's name.

Solution:

```swift
class Person {
    var name: String
    var age: Int
    var gender: String

    init(name: String, age: Int, gender: String) {
        self.name = name
        self.age = age
        self.gender = gender
    }

    func introduce() {
        print("Hello, my name is \(name).")
    }
}
```

To test this class, you could create an instance of the **`Person`** class and
call the **`introduce`** method:

```swift
let john = Person(name: "John", age: 30, gender: "Male")
john.introduce() // prints "Hello, my name is John."
```

This task is designed to test the basic understanding of object-oriented
programming (OOP) concepts, such as creating a class, defining properties and
methods, and initializing objects.

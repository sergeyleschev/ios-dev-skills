# Task 5

Task: Create a class called **`Person`** with properties **`name`** and
**`age`**. Create a subclass called **`Student`** that inherits from
**`Person`** and has an additional property called **`school`**. Create an
instance of **`Student`** and print out its name, age, and school.

Solution:

```swift
class Person {
    var name: String
    var age: Int

    init(name: String, age: Int) {
        self.name = name
        self.age = age
    }
}

class Student: Person {
    var school: String

    init(name: String, age: Int, school: String) {
        self.school = school
        super.init(name: name, age: age)
    }
}

let john = Student(name: "John", age: 20, school: "XYZ University")
print("\(john.name), \(john.age), \(john.school)")
```

Difference from Junior 2 level: In this task, the developer is required to
understand and apply inheritance in object-oriented programming. The creation of
a subclass and its initialization with **`super.init`** are key indicators of
understanding this concept.

# Task 1

Task: Create a class called **`Person`** with properties **`name`** and
**`age`**. Then create a subclass called **`Student`** that inherits from
**`Person`** and adds a property **`grade`**. Finally, create an instance of
**`Student`** and print out their name, age, and grade.

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
    var grade: Int

    init(name: String, age: Int, grade: Int) {
        self.grade = grade
        super.init(name: name, age: age)
    }
}

let student = Student(name: "John", age: 18, grade: 95)
print("Name: \(student.name), Age: \(student.age), Grade: \(student.grade)")
```

Difference from Junior 1: The Junior 2 developer should be able to understand
and implement basic inheritance and subclassing concepts, which is demonstrated
by the creation of the **`Student`** subclass. They should also be able to use
the **`super`** keyword to call the superclass's initializer. Additionally, the
Junior 2 developer should be able to create instances of classes with multiple
properties and print out the values of those properties, as shown in the
**`print`** statement at the end of the solution.

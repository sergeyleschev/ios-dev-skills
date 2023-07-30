# Task 5

Task: Create a **`Person`** class with properties **`firstName`** and
**`lastName`**, and a computed property **`fullName`** that returns the full
name of the person. Then create a **`Student`** subclass of **`Person`** with an
additional property **`grade`** that represents the student's grade level.
Finally, create an instance of **`Student`** and print out their full name and
grade.

Solution:

```swift
class Person {
    var firstName: String
    var lastName: String

    var fullName: String {
        return "\(firstName) \(lastName)"
    }

    init(firstName: String, lastName: String) {
        self.firstName = firstName
        self.lastName = lastName
    }
}

class Student: Person {
    var grade: Int

    init(firstName: String, lastName: String, grade: Int) {
        self.grade = grade
        super.init(firstName: firstName, lastName: lastName)
    }
}

let student = Student(firstName: "John", lastName: "Doe", grade: 10)
print("\(student.fullName), grade \(student.grade)")
```

Difference from Junior 1: The Junior 2 developer should be able to create and
use subclasses, as demonstrated by the creation of the **`Student`** subclass of
**`Person`**. They should also be able to use initializers and superclasses, as
shown in the initialization of the **`Student`** instance and the use of
**`super.init()`** to initialize the superclass properties. Finally, they should
be able to create and use computed properties, which is demonstrated by the
creation of the **`fullName`** computed property on **`Person`**.

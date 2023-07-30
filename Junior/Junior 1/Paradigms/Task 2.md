# Task 2

Task: Create a class called "Person" with properties for "name" and "age". Add a
method called "introduce" that prints out a message introducing the person with
their name and age.

Solution:

```swift
class Person {
    var name: String
    var age: Int

    init(name: String, age: Int) {
        self.name = name
        self.age = age
    }

    func introduce() {
        print("Hi, my name is \(name) and I am \(age) years old.")
    }
}
```

Explanation: This task tests the candidate's understanding of object-oriented
programming (OOP) concepts such as classes, properties, and methods. The
solution defines a simple "Person" class with two properties, "name" and "age",
and a method called "introduce" that prints out a message introducing the person
with their name and age. The solution demonstrates the use of the "init" method
to initialize the properties of the class and the use of string interpolation to
print out the message in the "introduce" method.

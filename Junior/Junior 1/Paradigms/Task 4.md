# Task 4

Task: Create a class named "Person" with two properties: "name" and "age". The
class should have a function named "introduce" that prints out a message
introducing the person with their name and age.

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

let person1 = Person(name: "John", age: 30)
person1.introduce() // Output: Hi, my name is John and I am 30 years old.
```

Explanation: This task tests the basic understanding of Object-Oriented
Programming concepts like classes, properties, and methods. The solution creates
a class named "Person" with two properties: "name" and "age". It also has a
function named "introduce" that prints out a message introducing the person with
their name and age. The solution also demonstrates how to create an instance of
the class and call its methods.

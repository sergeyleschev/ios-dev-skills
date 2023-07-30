# Task 3

Task: Create a class called **`Animal`** with a property **`name`** and a method
**`makeSound()`**. Then create a subclass called **`Dog`** that inherits from
**`Animal`** and overrides the **`makeSound()`** method to print "Woof".
Finally, create an instance of **`Dog`** and call the **`makeSound()`** method.

Solution:

```swift
class Animal {
    var name: String

    init(name: String) {
        self.name = name
    }

    func makeSound() {
        print("Generic animal sound")
    }
}

class Dog: Animal {
    override func makeSound() {
        print("Woof")
    }
}

let dog = Dog(name: "Fido")
dog.makeSound()
```

Difference from Junior 1: The Junior 2 developer should be able to understand
and implement method overriding, which is demonstrated by the creation of the
**`Dog`** subclass and the override of the **`makeSound()`** method. They should
also be able to create and use instances of classes with methods, as shown in
the creation of the **`dog`** instance and the call to the **`makeSound()`**
method.

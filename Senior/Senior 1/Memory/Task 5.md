# Task 5

Task: Given the following code, identify and fix any potential memory leaks:

```swift
class Person {
  var name: String
  var age: Int

  init(name: String, age: Int) {
    self.name = name
    self.age = age
  }

  func introduce() {
    print("Hello, my name is \(name) and I'm \(age) years old.")
  }
}

class ViewController: UIViewController {
  var person: Person?

  override func viewDidLoad() {
    super.viewDidLoad()
    person = Person(name: "John", age: 30)
    person?.introduce()
  }
}
```

Solution: There is a potential memory leak in the **`ViewController`** class.
The **`person`** property is a strong reference to the **`Person`** instance
created in the **`viewDidLoad`** method, and is never set to **`nil`**. To fix
this, we can set **`person`** to **`nil`** in the **`deinit`** method of
**`ViewController`**:

```swift
class ViewController: UIViewController {
  var person: Person?

  override func viewDidLoad() {
    super.viewDidLoad()
    person = Person(name: "John", age: 30)
    person?.introduce()
  }

  deinit {
    person = nil
  }
}
```

This ensures that the **`Person`** instance is deallocated when the
**`ViewController`** instance is deallocated.

# Task 5

Task: Create a simple calculator app that follows the MVC design pattern. The
calculator should have two text fields for input and one label for output. The
app should perform basic arithmetic operations (addition, subtraction,
multiplication, and division) on the two input values and display the result in
the output label.

Solution: First, create a model file called Calculator.swift:

```swift
import Foundation

class Calculator {

    func add(_ a: Double, _ b: Double) -> Double {
        return a + b
    }

    func subtract(_ a: Double, _ b: Double) -> Double {
        return a - b
    }

    func multiply(_ a: Double, _ b: Double) -> Double {
        return a * b
    }

    func divide(_ a: Double, _ b: Double) -> Double {
        return a / b
    }
}
```

Then, create a view controller file called CalculatorViewController.swift:

```swift
import UIKit

class CalculatorViewController: UIViewController {

    @IBOutlet weak var input1TextField: UITextField!
    @IBOutlet weak var input2TextField: UITextField!
    @IBOutlet weak var outputLabel: UILabel!

    let calculator = Calculator()

    @IBAction func calculateButtonTapped(_ sender: UIButton) {
        guard let input1 = Double(input1TextField.text ?? "") else { return }
        guard let input2 = Double(input2TextField.text ?? "") else { return }

        let result = calculator.add(input1, input2)
        outputLabel.text = "\(result)"
    }
}
```

Finally, create a storyboard with two text fields, one label, and one button.
Connect the outlets and action to the view controller.

Differences between Junior 2 and Junior 3 levels:

At the Junior 3 level, a developer should have a deeper understanding of the MVC
design pattern and how to implement it in iOS development. They should be able
to explain the responsibilities of each component (model, view, and controller)
and how they interact with each other. Additionally, they should be able to
identify situations where MVC is appropriate and where other design patterns may
be more suitable. They should also be familiar with common pitfalls of MVC, such
as view controllers becoming too bloated with business logic.

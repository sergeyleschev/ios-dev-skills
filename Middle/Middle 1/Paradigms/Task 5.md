# Task 5

Task: Given an array of integers, implement a function that returns the sum of
all even numbers in the array, using Functional Reactive Programming (FRP)
concepts.

Solution:

```swift
import Foundation
import Combine

let numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]

let evenSum = numbers.publisher
    .filter { $0 % 2 == 0 }
    .reduce(0, +)

evenSum.sink { sum in
    print("The sum of even numbers is \(sum)")
}
```

In this solution, we use the **`publisher`** method from the Combine framework
to create a reactive stream of values from the **`numbers`** array. Then we use
the **`filter`** operator to keep only the even numbers and the **`reduce`**
operator to calculate their sum. Finally, we subscribe to the result using the
**`sink`** method and print the value of the sum.

This solution showcases the use of FRP concepts like reactive streams,
operators, and subscribers to solve the problem in a concise and efficient way.
It also demonstrates the ability to leverage third-party frameworks like Combine
to implement FRP in Swift.

Compared to the Junior 3 level test tasks, this one requires a deeper
understanding of functional programming and reactive programming concepts, and
the ability to use them to solve real-world problems. It also requires
familiarity with third-party frameworks and libraries commonly used in iOS
development.

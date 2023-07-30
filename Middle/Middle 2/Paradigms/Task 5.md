# Task 5

Task: Given a list of integers, write a function that returns the sum of all
even numbers in the list using FRP.

Solution:

```swift
import Foundation
import Combine

func sumOfEvenNumbers(_ numbers: [Int]) -> AnyPublisher<Int, Never> {
    return numbers.publisher
        .filter { $0 % 2 == 0 }
        .reduce(0, +)
        .eraseToAnyPublisher()
}

let numbers = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
let sumPublisher = sumOfEvenNumbers(numbers)

sumPublisher.sink { value in
    print("Sum of even numbers: \(value)")
}.store(in: &cancellables)
```

Differences from the previous Middle 1 level task:

-   This task requires the use of Combine framework to create a publisher for
    summing even numbers, which is a more advanced topic than just using
    functional reactive programming concepts.
-   The use of **`eraseToAnyPublisher()`** method is needed to type erase the
    publisher and make it easier to use with the **`sink`** method, which may be
    new to the developer at this level.

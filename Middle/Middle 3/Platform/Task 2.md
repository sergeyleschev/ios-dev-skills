# Task 2

Task: You have a list of employees with their names and salaries stored in a
dictionary. Write a function that takes this dictionary and returns the name of
the employee with the highest salary.

Solution:

```swift
func highestPaidEmployee(employees: [String: Int]) -> String? {
    var highestPaidEmployee: String?
    var highestSalary = 0

    for (employee, salary) in employees {
        if salary > highestSalary {
            highestSalary = salary
            highestPaidEmployee = employee
        }
    }

    return highestPaidEmployee
}
```

Differences from Middle 2 level:

-   This task involves more complex dictionary manipulation, including iteration
    and comparison of values.
-   The solution involves the use of conditional statements to compare values
    and assign variables, demonstrating a deeper understanding of control flow.
-   The solution is designed to be more modular, with a dedicated function to
    perform the necessary calculations and return the desired result.

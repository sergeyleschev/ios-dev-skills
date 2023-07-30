# Task 2

## **Task:**

Write a function **`removeDuplicates`** that takes an array of integers as input
and returns an array with duplicates removed.

For example, if the input is **`[1, 2, 2, 3, 3, 3, 4, 5, 5]`**, the function
should return **`[1, 2, 3, 4, 5]`**.

This function should use a **`Set`** to keep track of the unique integers in the
input array.

### **Solution:**

```swift
func removeDuplicates(_ array: [Int]) -> [Int] {
    var set = Set<Int>()
    var result = [Int]()
    for element in array {
        if !set.contains(element) {
            set.insert(element)
            result.append(element)
        }
    }
    return result
}
```

In this solution, we create a **`Set`** called **`set`** to keep track of the
unique integers in the input array. We also create an empty array called
**`result`** to store the unique integers.

We then iterate over each element in the input array using a **`for`** loop. For
each element, we check if it is already in the **`set`**. If it is not, we add
it to the **`set`** and append it to the **`result`** array.

Finally, we return the **`result`** array with duplicates removed.

The key difference between this task and the previous ones is that it requires
the use of a **`Set`** to solve. The developer must be able to understand when
to use a **`Set`** instead of an **`Array`** or **`Dictionary`** and be
comfortable with the basic operations of a **`Set`** such as **`insert`** and
**`contains`**.

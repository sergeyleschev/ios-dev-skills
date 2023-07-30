# Task 4

Task: Given an array of integers, write a function that sorts the array in
descending order using a parallel merge sort algorithm. The function should use
Grand Central Dispatch (GCD) to split the array into multiple parts and sort
them concurrently on different threads. The final merge should also happen on a
background thread and the sorted array should be returned on the main thread.

Solution:

```swift
func parallelMergeSort(_ array: [Int], completion: @escaping ([Int]) -> Void) {
    let backgroundQueue = DispatchQueue.global(qos: .background)
    let mainQueue = DispatchQueue.main

    if array.count <= 1 {
        completion(array)
        return
    }

    let midIndex = array.count / 2
    let leftArray = Array(array[0..<midIndex])
    let rightArray = Array(array[midIndex..<array.count])

    var leftResult: [Int]?
    var rightResult: [Int]?

    // Sort the left half of the array on a background thread
    backgroundQueue.async {
        self.parallelMergeSort(leftArray) { result in
            leftResult = result
        }
    }

    // Sort the right half of the array on a background thread
    backgroundQueue.async {
        self.parallelMergeSort(rightArray) { result in
            rightResult = result
        }
    }

    // Wait for both halves to finish sorting before merging them
    backgroundQueue.async {
        while leftResult == nil || rightResult == nil {
            // Sleep to avoid excessive CPU usage
            Thread.sleep(forTimeInterval: 0.1)
        }

        let result = self.merge(leftResult!, rightResult!)

        // Return the sorted array on the main thread
        mainQueue.async {
            completion(result)
        }
    }
}

private func merge(_ leftArray: [Int], _ rightArray: [Int]) -> [Int] {
    var leftIndex = 0
    var rightIndex = 0
    var result: [Int] = []

    while leftIndex < leftArray.count && rightIndex < rightArray.count {
        if leftArray[leftIndex] > rightArray[rightIndex] {
            result.append(leftArray[leftIndex])
            leftIndex += 1
        } else {
            result.append(rightArray[rightIndex])
            rightIndex += 1
        }
    }

    result += Array(leftArray[leftIndex..<leftArray.count])
    result += Array(rightArray[rightIndex..<rightArray.count])

    return result
}
```

Differences from the previous level (Middle 2):

-   The solution uses a parallel merge sort algorithm to sort an array of
    integers, which requires more advanced knowledge of algorithms and data
    structures
-   The solution uses Grand Central Dispatch to perform the sorting concurrently
    on different threads, which requires more advanced knowledge of
    multithreading and thread synchronization
-   The solution uses a sleep function to avoid excessive CPU usage, which
    requires more advanced knowledge of thread scheduling and resource
    management.

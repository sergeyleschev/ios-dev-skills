# Task 2

Task: You are given a dictionary that maps words to their frequency counts in a
text. Write a function to find the top k frequent words in the text. The
function should return an array of k most frequent words.

Example input:

```swift
let text = "The quick brown fox jumps over the lazy dog"
let k = 3
let wordCounts = ["the": 2, "quick": 1, "brown": 1, "fox": 1, "jumps": 1, "over": 1, "lazy": 1, "dog": 1]
```

Expected output:

```swift
swiftCopy code
["the", "quick", "brown"]
```

Function signature:

```swift
func topKFrequentWords(_ text: String, _ k: Int, _ wordCounts: [String: Int]) -> [String] {
  // your code here
}
```

Differences from Junior 1 level:

-   The problem involves processing a dictionary, which requires more advanced
    knowledge of data structures and algorithms.
-   The function signature now takes three parameters instead of one or two,
    which is an indication of more complex programming requirements.
-   The function name includes the word "top" and "frequent" to make it more
    clear what the function does. This is a good practice for writing clean and
    understandable code.
-   The solution involves more complex logic such as sorting the dictionary by
    values, selecting only the top k items, and converting the result into an
    array.

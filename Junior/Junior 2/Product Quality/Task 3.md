# Task 3

Task: Write a function that takes a string as input and returns a dictionary
where the keys are the unique words in the string and the values are the number
of times each word appears in the string.

Solution:

```swift
func countWords(_ input: String) -> [String: Int] {
    var wordCounts = [String: Int]()
    let words = input.components(separatedBy: .whitespacesAndNewlines)
    for word in words {
        wordCounts[word, default: 0] += 1
    }
    return wordCounts
}
```

Explanation:

This function takes a string as input and first creates an empty dictionary to
store the word counts. It then uses the **`components(separatedBy:)`** method to
split the string into an array of words based on whitespace and newline
characters. Finally, it loops through the array of words and uses the
dictionary's **`default`** property to increment the count for each word.

Example usage:

```swift
let input = "apple banana cherry banana date"
let wordCounts = countWords(input)
print(wordCounts) // Output: ["apple": 1, "banana": 2, "cherry": 1, "date": 1]
```

Difference between Junior 1 and Junior 2:

The Junior 2 level developer's solution demonstrates a deeper understanding of
Swift's standard library and its methods. They use the
**`components(separatedBy:)`** method to split the input string into an array of
words instead of manually splitting the string using a loop or other string
methods. Additionally, the Junior 2 developer's code uses Swift's dictionary
**`default`** property to simplify the logic for incrementing word counts
instead of using an if statement or force-unwrapping optionals. Finally, the
Junior 2 developer's code is more concise as they avoid unnecessary steps like
declaring an empty array or using a for loop to iterate over the array. Overall,
the Junior 2 developer's solution is more advanced and efficient than that of
the Junior 1 developer.

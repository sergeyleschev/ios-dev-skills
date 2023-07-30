# Task 2

Task: Create a unit test for a function that retrieves and parses JSON data from
an API. The function should take in a URL as a parameter and return a custom
object with the parsed data. The custom object should have properties for each
value in the JSON data.

Solution:

```swift
func testFetchDataFromAPI() {
  // Given
  let url = URL(string: "https://example.com/data.json")
  let session = URLSession(configuration: .default)
  let promise = expectation(description: "Completion handler invoked")

  // When
  let task = session.dataTask(with: url!) { data, response, error in
    // Then
    guard let data = data else {
      XCTFail("No data received from API")
      return
    }

    do {
      let decoder = JSONDecoder()
      let parsedData = try decoder.decode(CustomObject.self, from: data)
      XCTAssertEqual(parsedData.propertyOne, expectedValueOne)
      XCTAssertEqual(parsedData.propertyTwo, expectedValueTwo)
      promise.fulfill()
    } catch {
      XCTFail("Error decoding data: \(error.localizedDescription)")
    }
  }

  task.resume()

  wait(for: [promise], timeout: 5)
}
```

In this solution, we are using XCTest to create a unit test for a function that
fetches and parses JSON data from an API. We are creating a URLSession to make
the network request, and then using the JSONDecoder to parse the data into a
custom object. We then assert that the properties of the custom object match the
expected values.

To differentiate a middle 3 developer from a middle 2 developer, the interviewer
should look for more complex unit tests that involve testing multiple components
and interactions between them, as well as a deep understanding of TDD and best
practices for writing effective unit tests. Additionally, a middle 3 developer
may be able to create more sophisticated UI tests using XCTest, including
testing accessibility and localization features.

# Task 1

Task:

You are given a class named **`NetworkingManager`** which handles network
requests. The class has a function named
**`fetchData(from url: URL, completion: @escaping (Result<Data, Error>) -> Void)`**
which takes a URL and a completion handler that returns a **`Result`** object
containing either the data returned from the request or an error.

Your task is to write a unit test for this function that checks if it returns
the expected data or error when given a mock URL and mock data.

Solution:

```swift
import XCTest
@testable import YourApp

class NetworkingManagerTests: XCTestCase {

    func testFetchData() {
        // Given
        let networkingManager = NetworkingManager()
        let mockURL = URL(string: "https://example.com")!
        let mockData = Data([0, 1, 0, 1])
        let expectedData = mockData

        // When
        let expectation = self.expectation(description: "Fetch data from URL")
        networkingManager.fetchData(from: mockURL) { result in
            switch result {
            case .success(let data):
                XCTAssertEqual(data, expectedData)
            case .failure(let error):
                XCTFail("Unexpected error: \(error)")
            }
            expectation.fulfill()
        }

        // Then
        waitForExpectations(timeout: 5, handler: nil)
    }
}
```

Differences that indicate development from Middle 2 to Middle 3:

-   Use of more advanced testing techniques such as test doubles (mocks, stubs,
    fakes) to isolate the system under test and increase test reliability.
-   More thorough testing of edge cases and error handling scenarios.
-   Better integration of testing into the development process, including
    automation of testing and incorporation of testing feedback into the
    development cycle.

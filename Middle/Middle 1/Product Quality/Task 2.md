# Task 2

Task: You are working on a project that involves fetching data from a remote API
and displaying it in a table view. Write a unit test that checks whether the
table view data source is correctly populated with the data fetched from the
API.

Solution:

```swift
class RemoteAPIManager {
    func fetchData(completion: @escaping ([String]) -> Void) {
        // implementation of remote data fetching
    }
}

class TableViewController: UITableViewController {
    var data: [String] = []

    override func viewDidLoad() {
        super.viewDidLoad()
        let remoteAPIManager = RemoteAPIManager()
        remoteAPIManager.fetchData { [weak self] (data) in
            self?.data = data
            DispatchQueue.main.async {
                self?.tableView.reloadData()
            }
        }
    }

    override func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        return data.count
    }

    override func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
        let cell = tableView.dequeueReusableCell(withIdentifier: "Cell", for: indexPath)
        cell.textLabel?.text = data[indexPath.row]
        return cell
    }
}

class TableViewControllerTests: XCTestCase {
    var sut: TableViewController!

    override func setUpWithError() throws {
        sut = TableViewController()
        _ = sut.view // force load the view so that data is fetched from the API
    }

    func testTableViewDataSource() {
        // given
        let expectedData = ["Data1", "Data2", "Data3"]
        sut.data = expectedData

        // when
        let numberOfRows = sut.tableView.numberOfRows(inSection: 0)

        // then
        XCTAssertEqual(numberOfRows, expectedData.count)
    }
}
```

Differences: The key difference between a Junior and a Middle iOS Developer is
that a Middle Developer should be able to write unit tests and be familiar with
TDD (Test Driven Development). In this task, the developer is expected to write
a test that checks whether the table view data source is correctly populated
with the data fetched from the remote API. Additionally, the developer should
also have knowledge of using dependency injection to mock the API response and
perform the test in isolation.

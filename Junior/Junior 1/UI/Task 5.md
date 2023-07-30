# Task 5

Task:

Create a basic UI in Interface Builder for an app that displays a list of items.
The UI should consist of a table view that displays the items, with each item
showing its name and image.

Solution:

Step 1: Create a new XIB file called "ItemListViewController" and open it in
Interface Builder.

Step 2: Drag a table view onto the view and set its constraints so that it fills
the entire view.

Step 3: Create a UITableViewCell prototype called "ItemCell" and add an image
view and a label to the cell's content view.

Step 4: Set the constraints for the image view and label so that they are
properly positioned and sized within the cell.

Step 5: Create an outlet for the table view in the ItemListViewController class.

```swift
@IBOutlet weak var tableView: UITableView!
```

Step 6: In the viewDidLoad method of the ItemListViewController class, register
the "ItemCell" prototype with the table view and set the data source and
delegate to the view controller.

```swift
override func viewDidLoad() {
    super.viewDidLoad()

    tableView.register(UINib(nibName: "ItemCell", bundle: nil), forCellReuseIdentifier: "ItemCell")
    tableView.dataSource = self
    tableView.delegate = self
}
```

Step 7: Implement the UITableViewDataSource and UITableViewDelegate protocols in
the ItemListViewController class.

```swift
extension ItemListViewController: UITableViewDataSource {
    func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        // return the number of items to display
    }

    func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
        let cell = tableView.dequeueReusableCell(withIdentifier: "ItemCell", for: indexPath) as! ItemCell
        // configure the cell with the item's name and image
        return cell
    }
}

extension ItemListViewController: UITableViewDelegate {
    func tableView(_ tableView: UITableView, didSelectRowAt indexPath: IndexPath) {
        // handle item selection
    }
}
```

Step 8: Run the app to test the UI and ensure that the list of items is
displayed correctly with each item showing its name and image.

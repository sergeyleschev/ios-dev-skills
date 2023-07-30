# Task 4

Task:

Create a basic UI in autolayout code for an app that displays a list of items.
The UI should consist of a table view that displays the items, with each item
showing its name and image.

Solution:

Step 1: Create a new subclass of UIViewController called
"ItemListViewController".

Step 2: In the viewDidLoad method, create a table view and add it to the view.

```swift
let tableView = UITableView()
view.addSubview(tableView)
```

Step 3: Set the constraints for the table view so that it fills the entire view.

```swift
tableView.translatesAutoresizingMaskIntoConstraints = false
NSLayoutConstraint.activate([
    tableView.leadingAnchor.constraint(equalTo: view.leadingAnchor),
    tableView.trailingAnchor.constraint(equalTo: view.trailingAnchor),
    tableView.topAnchor.constraint(equalTo: view.topAnchor),
    tableView.bottomAnchor.constraint(equalTo: view.bottomAnchor)
])
```

Step 4: Create a UITableViewCell subclass called "ItemCell".

Step 5: In the ItemCell class, add an image view and a label to the cell's
content view.

```swift
let imageView = UIImageView()
contentView.addSubview(imageView)

let label = UILabel()
contentView.addSubview(label)
```

Step 6: Set the constraints for the image view and label so that they are
properly positioned and sized within the cell.

```swift
imageView.translatesAutoresizingMaskIntoConstraints = false
NSLayoutConstraint.activate([
    imageView.leadingAnchor.constraint(equalTo: contentView.leadingAnchor),
    imageView.widthAnchor.constraint(equalToConstant: 50),
    imageView.heightAnchor.constraint(equalToConstant: 50),
    imageView.centerYAnchor.constraint(equalTo: contentView.centerYAnchor)
])

label.translatesAutoresizingMaskIntoConstraints = false
NSLayoutConstraint.activate([
    label.leadingAnchor.constraint(equalTo: imageView.trailingAnchor, constant: 8),
    label.trailingAnchor.constraint(equalTo: contentView.trailingAnchor),
    label.topAnchor.constraint(equalTo: contentView.topAnchor),
    label.bottomAnchor.constraint(equalTo: contentView.bottomAnchor)
])
```

Step 7: In the ItemListViewController class, set the table view's data source
and delegate to the view controller.

```swift
tableView.dataSource = self
tableView.delegate = self
```

Step 8: Implement the UITableViewDataSource and UITableViewDelegate protocols in
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

Step 9: Run the app to test the UI and ensure that the list of items is
displayed correctly with each item showing its name and image.

# Task 4

Task:

You have a view controller that displays a list of items. Each item has a name
and a category. You notice that when scrolling through the list, the app becomes
slower and sometimes even freezes. Use your knowledge of memory management to
identify and fix the issue.

Solution:

The issue is most likely caused by the creation of new views or objects when
scrolling through the list. To fix this, we can implement a technique called
cell reuse.

First, we need to register the cell reuse identifier in the viewDidLoad method:

```swift
override func viewDidLoad() {
    super.viewDidLoad()

    tableView.register(UITableViewCell.self, forCellReuseIdentifier: "cell")
}
```

Then, in the **`cellForRowAt`** method, we can dequeue a reusable cell and set
its values:

```swift
override func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
    let cell = tableView.dequeueReusableCell(withIdentifier: "cell", for: indexPath)

    let item = items[indexPath.row]

    cell.textLabel?.text = item.name
    cell.detailTextLabel?.text = item.category

    return cell
}
```

This way, we are reusing existing cells instead of creating new ones each time.
This can significantly improve the app's performance and avoid memory leaks
caused by creating too many objects.

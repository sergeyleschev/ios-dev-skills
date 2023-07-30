# Task 2

Task:

Create a simple app that allows the user to select a color from a list of
options. When the user selects a color, the background color of the app should
change to the selected color.

Technical Requirements:

-   Use a UITableView to display the list of color options.
-   Use a delegate pattern to communicate between the list view and the main
    view controller.

Solution:

1. First, create a protocol called **`ColorSelectionDelegate`** with the
   following method:

```swift
protocol ColorSelectionDelegate: AnyObject {
    func didSelectColor(_ color: UIColor)
}
```

2. Next, create a **`ColorOptionsViewController`** that displays a list of color
   options in a UITableView. Implement the UITableViewDataSource and
   UITableViewDelegate methods to display the color options using a custom
   UITableViewCell subclass.

```swift
class ColorOptionsViewController: UIViewController, UITableViewDataSource, UITableViewDelegate {

    var colors: [UIColor] = []
    weak var delegate: ColorSelectionDelegate?

    // Implement UITableViewDataSource and UITableViewDelegate methods here

    func tableView(_ tableView: UITableView, didSelectRowAt indexPath: IndexPath) {
        let selectedColor = colors[indexPath.row]
        delegate?.didSelectColor(selectedColor)
    }
}
```

3. In the main view controller, create an instance of the
   **`ColorOptionsViewController`** and present it when a button is tapped. Set
   the main view controller as the delegate of the
   **`ColorOptionsViewController`**.

```swift
class ViewController: UIViewController, ColorSelectionDelegate {

    @IBAction func changeColorButtonTapped(_ sender: UIButton) {
        let colorOptionsViewController = ColorOptionsViewController()
        colorOptionsViewController.delegate = self
        present(colorOptionsViewController, animated: true, completion: nil)
    }

    func didSelectColor(_ color: UIColor) {
        view.backgroundColor = color
    }
}
```

Differences from Junior 1 Level:

The solution for this task is a step above the previous Junior level task as it
involves passing data (the selected color) from a presented view controller back
to the presenting view controller using a delegate pattern. The
**`ColorSelectionDelegate`** protocol allows the
**`ColorOptionsViewController`** to communicate with the main view controller
and pass the selected **`UIColor`** object. Additionally, the solution requires
updating the background color of the main view controller's view, rather than
just a single element as in the previous Junior level task. This task requires a
deeper understanding of delegation and view controller communication than the
previous Junior level task.

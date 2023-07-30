# Task 4

Task: Create a screen that displays a list of items fetched from an API and
allows the user to tap on each item to see its details.

Solution:

1. Open Xcode and create a new project with a Single View App template.
2. In the storyboard, drag a table view onto the view controller.
3. Add constraints to make the table view take up the entire view.
4. Create a custom table view cell to display each item's information.
5. Create a model class to represent each item and parse the API response into
   an array of these items.
6. Implement the UITableViewDataSource and UITableViewDelegate protocols.
7. In the table view's data source methods, return the number of rows and the
   custom table view cell for each item.
8. In the table view's delegate method, handle the selection of a table view
   cell by presenting the details view controller.
9. In the details view controller, display the item's details using labels and
   appropriate UI controls.
10. Build and run the app to test the list and details screens.

Differences from Junior 2 level:

-   Junior 3 level should have a good understanding of API consumption and data
    parsing techniques.
-   Junior 3 level should be able to implement complex UI features, such as
    custom table view cells, to display the data.
-   Junior 3 level should be able to implement navigation and flow between
    screens.

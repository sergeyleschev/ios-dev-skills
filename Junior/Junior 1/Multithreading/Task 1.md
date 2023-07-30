# Task 1

Task: Create a simple iOS app that displays a list of items. Each item should
have a title and a subtitle. When the user taps on an item, a detail view should
be presented that displays the selected item's title and subtitle.

Solution:

1. Create a new Xcode project, selecting the "Single View App" template.
2. In the Main.storyboard file, add a Table View Controller and embed it in a
   Navigation Controller.
3. In the Table View Controller, create a prototype cell with a reuse identifier
   of "ItemCell". Add a Label and a Detail Label to the cell, and set their
   constraints so that they are centered vertically and horizontally within the
   cell's content view.
4. Create a new Swift file called "Item.swift". In this file, define a struct
   called "Item" with two properties: "title" and "subtitle".
5. In the Table View Controller's class, define an array of "Item" objects as a
   property. This will be the data source for the table view.
6. In the Table View Controller's viewDidLoad() method, populate the array with
   some sample data.
7. Implement the UITableViewDataSource protocol in the Table View Controller's
   class. Return the number of items in the array in the numberOfSections(in
   tableView: UITableView) method, and return a configured "ItemCell" in the
   tableView(\_ tableView: UITableView, cellForRowAt indexPath: IndexPath)
   method.
8. Implement the UITableViewDelegate protocol in the Table View Controller's
   class. In the tableView(\_ tableView: UITableView, didSelectRowAt indexPath:
   IndexPath) method, instantiate a new view controller and set its title and
   subtitle properties based on the selected item. Present the new view
   controller modally.
9. In the new view controller, add two labels and set their constraints so that
   they are centered vertically and horizontally within the view's content view.
   Set their text values to the title and subtitle properties passed in from the
   Table View Controller.

To make the app more performant, you can use the GCD framework to perform heavy
operations, such as loading images, on a background thread. Additionally, you
can use @synchronized blocks to ensure thread safety when accessing shared
resources, such as the array of "Item" objects.

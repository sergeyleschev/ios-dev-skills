# Task 2

Task: Create a simple iOS app that fetches data from an API and displays it in a
table view. The app should fetch the data on a background thread and update the
table view on the main thread.

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
6. In the Table View Controller's viewDidLoad() method, call a method to fetch
   data from the API on a background thread.
7. In the fetch data method, use URLSession to make a request to the API and
   parse the response data into an array of "Item" objects.
8. Once the data has been parsed, update the array of "Item" objects on the main
   thread using DispatchQueue.main.async.
9. In the Table View Controller's class, implement the UITableViewDataSource
   protocol to display the items in the table view.
10. In the cellForRowAt method, dequeue a reusable cell and set its text labels
    to the corresponding item's title and subtitle properties.
11. Run the app and verify that the data is displayed correctly in the table
    view.

To make the app more performant, you can use asyncAfter() method to load data
after delay. Also, use @synchronized blocks to ensure thread safety when
accessing shared resources, such as the array of "Item" objects.

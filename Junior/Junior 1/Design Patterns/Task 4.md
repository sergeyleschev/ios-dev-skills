# Task 4

Task:

Create a simple iOS app that displays a list of items in a table view. The items
should be fetched from a remote API and displayed in the table view. Use the MVC
design pattern to implement this functionality.

Solution:

Here's a simple solution that uses the MVC design pattern:

1. Create a new Xcode project and choose the Single View App template.
2. Delete the Main.storyboard file and remove the reference to it from the
   Info.plist file.
3. Create a new UITableViewController subclass for the table view controller and
   set it as the root view controller of the window in the AppDelegate.
4. Create a new model class that represents the data we want to display in the
   table view. This class should have a method to fetch the data from the remote
   API.
5. Use the UITableViewDataSource and UITableViewDelegate protocols to populate
   the table view with data and configure the cells.

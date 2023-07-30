# Task 4

Task: Create a custom view that displays a list of items in a table view, and
allows for dynamic cell height based on the content of the cell.

Solution:

1. Create a custom UIView subclass that includes a UITableView.
2. Implement the UITableViewDataSource and UITableViewDelegate protocols in the
   view subclass.
3. In the UITableViewDataSource methods, populate the table view with the list
   of items.
4. In the UITableViewDelegate method heightForRowAt, calculate the height of the
   cell based on the content of the cell.
5. In the UITableViewDelegate method estimatedHeightForRowAt, return a
   reasonable estimate of the cell height for better scrolling performance.
6. Use the UITableViewAutomaticDimension constant as the row height to allow for
   dynamic cell height.
7. Add any desired customization to the table view cells in the UITableViewCell
   subclass.
8. Use the custom view in your app wherever you need to display a list of items
   with dynamic cell height.

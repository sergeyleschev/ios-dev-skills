# Task 2

Task:

Create an iOS app that retrieves data from an API and displays it in a table
view. The app should use multithreading to ensure that the UI remains responsive
while the data is being downloaded.

Solution:

1. Create a new Xcode project and add a UITableView to the main view controller.
2. Create a custom UITableViewCell subclass to display the data retrieved from
   the API.
3. Define a property to store the data retrieved from the API.
4. Create a function to download the data on a background thread using
   URLSession and update the property with the retrieved data.
5. Once the data has been retrieved, reload the table view on the main thread
   using DispatchQueue.main.async.
6. In the viewDidLoad() method, call the function to download the data.
7. Implement the UITableViewDataSource methods to display the retrieved data in
   the table view cells.
8. Run the app and verify that the data is downloaded and displayed correctly in
   the table view.

Differences between Junior 1 and Junior 2 level:

At Junior 2 level, the developer is expected to have a deeper understanding of
concurrency and synchronization techniques, such as using semaphores and locks,
to ensure thread safety and prevent race conditions. Additionally, the developer
is expected to be able to optimize app performance by minimizing the number of
unnecessary network requests and using techniques such as pagination to load
large amounts of data efficiently.

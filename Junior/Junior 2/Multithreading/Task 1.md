# Task 1

Task:

Create a simple iOS app that displays a list of images downloaded from a server.
Each image should be displayed in a collection view cell, and the images should
be downloaded asynchronously on a background thread.

Solution:

1. Create a new Xcode project, selecting the "Single View App" template.
2. In the Main.storyboard file, add a Collection View to the view controller.
3. Create a custom UICollectionViewCell subclass to display the images.
4. Define a property to store the image data for each cell.
5. Create a function to download the image data for each cell on a background
   thread using URLSession.
6. Once the image data has been downloaded, update the cell's image view on the
   main thread using DispatchQueue.main.async.
7. In the viewDidLoad() method, set up the collection view and call the function
   to download the image data for each cell.
8. Run the app and verify that the images are downloaded and displayed correctly
   in the collection view.

Differences between Junior 1 and Junior 2 level:

At Junior 2 level, the developer is expected to have a better understanding of
multithreading concepts and use more advanced techniques such as Grand Central
Dispatch (GCD) to manage asynchronous tasks. Additionally, the developer is
expected to write more efficient and performant code by using techniques such as
lazy loading and caching to avoid unnecessary downloads and improve app
responsiveness.

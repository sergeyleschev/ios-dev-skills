# Task 5

Task: Create a simple iOS app that allows users to enter a URL and displays the
page title after it has been loaded. The loading of the page title should be
performed on a background thread, and the title should be displayed on the main
thread.

Solution:

1. Create a new Xcode project, selecting the "Single View App" template.
2. In the Main.storyboard file, add a Text Field and a Button to the view
   controller.
3. In the view controller's class, define a property to store the page title.
4. Create a function to load the page title from the URL on a background thread
   using URLSession and HTML parsing.
5. Once the page title has been loaded, update the page title on the main thread
   using DispatchQueue.main.async.
6. In the button's action method, get the URL from the text field and call the
   function to load the page title.
7. In the function to load the page title, use a do-catch block to handle any
   errors that may occur during the loading process.
8. Run the app and verify that the page title is displayed correctly.

To make the app more performant, you can use asyncAfter() method to load the
page title after delay. Additionally, you can use @synchronized blocks to ensure
thread safety when accessing shared resources, such as the page title data.

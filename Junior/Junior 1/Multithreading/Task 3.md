# Task 3

Task: Create a simple iOS app that allows users to download an image from a URL
and display it on the screen. The download should be performed on a background
thread, and the image should be displayed on the main thread.

Solution:

1. Create a new Xcode project, selecting the "Single View App" template.
2. In the Main.storyboard file, add an Image View to the view controller.
3. In the view controller's class, define a property to store the image
   downloaded from the URL.
4. Create a function to download the image from the URL on a background thread
   using URLSession.
5. Once the image has been downloaded, update the image view on the main thread
   using DispatchQueue.main.async.
6. In the viewDidLoad() method, call the function to download the image from the
   URL.
7. Run the app and verify that the image is displayed correctly.

To make the app more performant, you can use asyncAfter() method to download the
image after delay. Additionally, you can use @synchronized blocks to ensure
thread safety when accessing shared resources, such as the image data.

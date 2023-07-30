# Task 4

Task: You are working on a large iOS app that has several view controllers. You
noticed that one of the view controllers is causing a memory leak. The view
controller is a table view controller that displays a list of items. Each item
has an image and some text. When you scroll the table view, the images are
downloaded from the network and displayed in the cell. However, when you scroll
back up, the images are not being released from memory.

Solution: To fix the memory leak in the table view controller, you can implement
the following steps:

1. Use a caching mechanism for downloaded images. This will help to reduce the
   number of network requests when the user scrolls back up the table view.
2. Implement lazy loading for images. Instead of loading all the images at once,
   load only the images that are visible on the screen. This can be done by
   checking if the cell is visible in the table view's visibleCells array.
3. Override the prepareForReuse method of the table view cell and cancel any
   pending image downloads. This will ensure that images are not loaded for
   cells that are no longer visible on the screen.
4. Use weak references for any objects that are causing retain cycles. In this
   case, you should use a weak reference for the table view controller in the
   image download completion handler.

By implementing these steps, you can fix the memory leak in the table view
controller and improve the performance of the app. As a senior developer, you
should also consider profiling the app using tools like Instruments to identify
any other memory issues in the app.

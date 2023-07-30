# Task 3

Create a basic UI in Interface Builder (xib) or autolayout code for an app that
displays a product detail page. The UI should consist of an image view that
displays the product image, a label that displays the product name, and a button
to add the product to a cart.

Solution:

Step 1: Create a new xib file or programmatically create a UIView subclass.

Step 2: Drag and drop an Image View object onto the View. Adjust its position
and size as desired.

Step 3: Set the Image View's image to the product image.

Step 4: Drag and drop a Label object onto the View. Adjust its position and size
as desired.

Step 5: Set the Label's text to the product name.

Step 6: Drag and drop a Button object onto the View. Adjust its position and
size as desired.

Step 7: Set the Button's title to "Add to Cart".

Step 8: Add constraints to the Image View, Label, and Button objects so that
they are properly positioned and sized on different screen sizes.

Step 9: Create a new subclass of UIViewController called
"ProductDetailViewController".

Step 10: Open the xib file or programmatically create the view controller's view
and add the Image View, Label, and Button objects to it.

Step 11: Connect the Image View, Label, and Button objects to the
ProductDetailViewController class by control-dragging from the object to the
corresponding property or action in the class.

Step 12: Implement the add to cart button action in the
ProductDetailViewController class by adding the product to the cart.

Step 13: Run the app to test the UI and ensure that the product detail page is
displayed correctly and the add to cart button works properly.

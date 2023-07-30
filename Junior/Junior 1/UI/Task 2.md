# Task 2

Task:

Create a basic UI in Interface Builder (xib) for an app that allows users to
create a profile. The UI should consist of a form with text fields for the
user's name, email, and password, as well as a button to submit the form.

Solution:

Step 1: Create a new xib file by selecting File -> New -> File -> User Interface
-> View.

Step 2: Drag and drop a Label object onto the View, and set its text to "Create
Profile". Adjust its position and size as desired.

Step 3: Drag and drop three Text Field objects onto the View. Set their
placeholder text to "Name", "Email", and "Password", respectively. Adjust their
positions and sizes as desired.

Step 4: Drag and drop a Button object onto the View. Set its title to "Submit".
Adjust its position and size as desired.

Step 5: Add constraints to the Label, Text Field, and Button objects so that
they are properly positioned and sized on different screen sizes.

Step 6: Create a new subclass of UIViewController called
"CreateProfileViewController".

Step 7: Open the xib file and set its File's Owner to the
CreateProfileViewController class.

Step 8: Connect the Label, Text Field, and Button objects to the
CreateProfileViewController class by control-dragging from the object to the
corresponding property or action in the class.

Step 9: Implement the submit button action in the CreateProfileViewController
class by retrieving the text entered in the text fields and creating a new user
profile object with that information.

Step 10: Run the app to test the UI and ensure that the form is displayed
correctly and the submit button works properly.

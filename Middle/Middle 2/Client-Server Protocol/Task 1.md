# Task 1

Task: Implement the ability to send and receive images in the WebSocket-based
real-time chat.

Solution:

To send and receive images in the WebSocket-based real-time chat, we can follow
these steps:

1. Create a UI element (e.g. button) to allow the user to select an image from
   their device's photo library.
2. Convert the selected image to Data format using the UIImageJPEGRepresentation
   method.
3. Create a JSON object that includes the image data, sender ID, and message
   type (e.g. "image").
4. Send the JSON object to the server using the WebSocket send() method.
5. On the receiving end, parse the JSON object to extract the image data, sender
   ID, and message type.
6. Convert the received image data to a UIImage using the UIImage(data:)
   initializer.
7. Display the received image in the chat view.

Differences from Middle 1 level:

This task requires the developer to have a deeper understanding of handling
image data and parsing JSON objects. Additionally, the developer must be able to
display the received image in the chat view. The task also involves more complex
UI design, as it requires a button to allow the user to select an image from
their device's photo library. Finally, the task requires the developer to
implement a more robust error handling mechanism to handle any errors that may
occur during the image sending and receiving process.

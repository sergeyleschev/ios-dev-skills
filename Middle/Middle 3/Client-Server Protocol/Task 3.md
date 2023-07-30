# Task 3

Task: Implement a WebSocket-based real-time chat application with support for
sending images and displaying message timestamps. Use the Swift, Foundation, and
UIKit frameworks. Ensure that the app supports offline message syncing when the
user goes back online.

Solution:

To implement this task, the developer needs to have a strong understanding of
websockets, GCD (Grand Central Dispatch), image handling, message timestamps,
and data persistence. Here's a high-level overview of the steps involved in
completing this task:

1. Create a WebSocket connection to the server using URLSessionWebSocketTask.
2. Implement a chat UI with support for sending text messages and images.
3. Handle image selection using UIImagePickerController.
4. Display message timestamps in the chat UI.
5. Use Core Data or another data persistence framework to store messages when
   the user is offline and sync them when the user goes back online.

The main difference between this task and the previous middle-level tasks is the
addition of image handling, message timestamps, and offline message syncing. The
developer should be able to handle these new features efficiently and ensure a
smooth user experience.

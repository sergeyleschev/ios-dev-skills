# Task 5

### **Task**

You need to create a chat application that supports sending and receiving
messages in real-time using the WebSocket protocol. The app should allow users
to create new chats and join existing ones by entering a chat ID.

Additionally, the app should display a list of active users in the current chat
and show when users are typing a message. Users should also be able to upload
and send images in their messages.

### **Solution**

To create the chat application, we will use the WebSocket protocol to establish
a connection between the client and server. We will create a WebSocket manager
class that handles the communication between the client and server.

The app will have a main view controller that displays a list of chats that the
user is currently in or can join. When the user selects a chat, the app will
display a chat view controller that shows the list of messages in that chat and
allows the user to send new messages.

To support real-time updates, the app will use WebSockets to listen for new
messages and update the chat view controller when new messages are received. The
app will also use WebSockets to notify other users when the user is typing a
message.

To support image uploads, we will create a separate view controller that allows
the user to select an image from their photo library and upload it to the
server. The app will then include a link to the uploaded image in the message
sent to other users.

To show active users in the current chat, the app will use a separate WebSocket
connection to the server to listen for updates to the list of active users. The
app will then display the list of active users in the chat view controller.

### **Differences from Middle Level**

The Senior level developer would be expected to have a more in-depth
understanding of the WebSocket protocol and how to use it to create real-time
applications. Additionally, they would be expected to have experience working
with more complex UI features, such as uploading and displaying images, as well
as integrating multiple WebSocket connections into a single application.

In the solution provided, we use multiple WebSocket connections to support
real-time updates and image uploads, and we also display a list of active users
in the current chat. These features would be expected from a Senior level
developer, along with a more robust implementation that can handle errors and
edge cases.

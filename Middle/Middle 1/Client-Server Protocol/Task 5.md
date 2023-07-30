# Task 5

Task: Build a simple iOS app that connects to a WebSocket server and receives
real-time updates to display to the user. The app should allow the user to input
a username and connect to the server. Once connected, the app should display any
incoming messages in real-time and allow the user to send messages to the
server.

Solution:

To solve this task, you can follow these steps:

1. Create a new Xcode project and select "Single View App" as the template.
2. Add the following dependencies to your project using Swift Package Manager:
    - Starscream: a WebSocket client library
    - SwiftyJSON: a library for parsing JSON data
3. In your ViewController, import Starscream and SwiftyJSON.
4. Add properties for a WebSocket object, a text view to display incoming
   messages, a text field for user input, and a button to connect to the server.
5. In viewDidLoad, create a WebSocket object and set the delegate to self. Also,
   add an observer for the keyboard to adjust the layout when the keyboard
   appears.
6. Implement the WebSocketDelegate protocol to handle the following events:
    - When the connection is established, send a message to the server with the
      user's username.
    - When a message is received, parse the JSON data and append the message to
      the text view.
7. Implement the IBActions for the text field and button to send messages to the
   server.
8. Build and run the app, and test it by connecting to a WebSocket server and
   sending/receiving messages.

Differences from Junior 3 level:

To successfully complete this task, a Middle 1 level developer should be
familiar with the following concepts:

-   WebSocket communication protocol and how it differs from traditional HTTP
    requests
-   Asynchronous programming using delegates and callbacks
-   Parsing JSON data using a third-party library
-   UI layout and constraints
-   Swift Package Manager for managing dependencies

Compared to a Junior 3 level developer, a Middle 1 level developer should be
able to implement a more complex app with real-time data updates, as well as
handle more advanced concepts such as asynchronous programming and third-party
libraries.

# Task 2

Task: Implement a real-time chat application using WebSockets. The application
should allow users to connect to a WebSocket server and send/receive messages in
real-time. The UI should be clean and user-friendly, and the chat messages
should be displayed in a way that is easy to read and follow.

Solution:

1. Create a new Xcode project with a single view application template.
2. Import the Starscream library to handle WebSocket communication.
3. Create a WebSocket instance and connect to the server in the viewDidLoad()
   method of your view controller.

```swift
import Starscream

class ViewController: UIViewController, WebSocketDelegate {

    var socket: WebSocket!

    override func viewDidLoad() {
        super.viewDidLoad()

        socket = WebSocket(url: URL(string: "wss://yourwebsocketserver.com")!)
        socket.delegate = self
        socket.connect()
    }

    // WebSocket delegate methods go here
}
```

4. Implement the WebSocket delegate methods to handle incoming and outgoing
   messages.

```swift
func websocketDidConnect(socket: WebSocketClient) {
    print("WebSocket connected")
}

func websocketDidDisconnect(socket: WebSocketClient, error: Error?) {
    print("WebSocket disconnected: \(error?.localizedDescription ?? "")")
}

func websocketDidReceiveMessage(socket: WebSocketClient, text: String) {
    print("Received message: \(text)")
}

func websocketDidReceiveData(socket: WebSocketClient, data: Data) {
    print("Received data: \(data)")
}
```

5. Create a UI to display chat messages and allow the user to send messages.
6. When the user taps the send button, send the message to the WebSocket server.

```swift
@IBAction func sendMessage() {
    let message = "Hello, World!"
    socket.write(string: message)
}
```

7. When a message is received from the WebSocket server, display it in the UI.

```swift
func websocketDidReceiveMessage(socket: WebSocketClient, text: String) {
    DispatchQueue.main.async {
        self.chatTextView.text += "\n\(text)"
    }
}
```

Differences that indicate the development of the developer to the Middle 1 level
from the Junior 3 level might include:

1. The ability to integrate third-party libraries like Starscream to handle more
   complex tasks.
2. The ability to design a clean and user-friendly UI.
3. The ability to handle WebSocket communication with a server and send/receive
   messages in real-time.
4. An understanding of asynchronous programming to handle WebSocket
   communication in the background thread and update the UI on the main thread.

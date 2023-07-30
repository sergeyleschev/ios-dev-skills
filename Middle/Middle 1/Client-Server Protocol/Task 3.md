# Task 3

Task:

You are tasked with implementing a chat feature in an existing iOS app using
WebSocket protocol for real-time communication. You need to use a third-party
library for handling WebSocket connections.

Write a function that will initialize a WebSocket connection to the server and
implement the WebSocketDelegate protocol to handle incoming messages. Your
function should also provide a way to send messages to the server.

Solution:

Here is a sample implementation for the function:

```swift
import Foundation
import Starscream

class ChatWebSocket {

    private var socket: WebSocket

    init(urlString: String) {
        guard let url = URL(string: urlString) else {
            fatalError("Invalid URL: \(urlString)")
        }

        self.socket = WebSocket(url: url)
        self.socket.delegate = self
    }

    func connect() {
        socket.connect()
    }

    func send(message: String) {
        socket.write(string: message)
    }
}

extension ChatWebSocket: WebSocketDelegate {

    func websocketDidConnect(socket: WebSocketClient) {
        print("WebSocket connected!")
    }

    func websocketDidDisconnect(socket: WebSocketClient, error: Error?) {
        print("WebSocket disconnected with error: \(error?.localizedDescription ?? "unknown error")")
    }

    func websocketDidReceiveMessage(socket: WebSocketClient, text: String) {
        print("Received message: \(text)")
    }

    func websocketDidReceiveData(socket: WebSocketClient, data: Data) {
        print("Received data: \(data)")
    }
}
```

This implementation uses the Starscream library for handling WebSocket
connections. The **`ChatWebSocket`** class initializes the WebSocket connection
and implements the **`WebSocketDelegate`** protocol to handle incoming messages.
The **`connect`** function connects to the WebSocket server, and the **`send`**
function sends messages to the server.

For the Middle-level developer, the interviewer should pay attention to the
following differences from the Junior-level 3 developer:

-   The Middle-level developer is expected to use a third-party library for
    handling WebSocket connections, such as Starscream or SocketRocket, rather
    than implementing the protocol from scratch.
-   The Middle-level developer should be able to handle incoming messages using
    the **`WebSocketDelegate`** protocol and distinguish between different types
    of incoming data (text or binary).
-   The Middle-level developer should be able to write unit tests for the
    WebSocket connection to ensure it is working as expected.

# Task 1

Task: Write a function that establishes a secure WebSocket connection to a video
chat server and sends and receives messages to initiate and participate in a
video chat session. The function should handle error cases and gracefully
disconnect from the server when the session is finished.

Solution:

```swift
import Foundation
import Starscream // a WebSocket library for Swift

class VideoChatSession {
    private var socket: WebSocket?

    func startSession() {
        guard let url = URL(string: "wss://videochatserver.com") else { return }
        var request = URLRequest(url: url)
        request.timeoutInterval = 5
        self.socket = WebSocket(request: request)
        self.socket?.delegate = self
        self.socket?.connect()
    }

    func endSession() {
        self.socket?.disconnect()
        self.socket = nil
    }

    func sendMessage(_ message: String) {
        self.socket?.write(string: message)
    }
}

extension VideoChatSession: WebSocketDelegate {
    func didReceive(event: WebSocketEvent, client: WebSocket) {
        switch event {
        case .connected(let headers):
            print("WebSocket is connected: \(headers)")
            // send message to initiate video chat session
            self.sendMessage("initiate_video_chat_session")
        case .disconnected(let reason, let code):
            print("WebSocket is disconnected: \(reason) with code: \(code)")
        case .text(let string):
            // handle incoming message
            print("Received text: \(string)")
        case .binary(let data):
            // handle incoming binary data
            print("Received data: \(data.count) bytes")
        case .pong(_):
            // handle pong message
            break
        case .ping(_):
            // handle ping message
            break
        case .error(let error):
            // handle error
            print("WebSocket encountered an error: \(error)")
        case .viabilityChanged(_):
            // handle viability change
            break
        case .reconnectSuggested(_):
            // handle reconnect suggestion
            break
        case .cancelled:
            // handle cancellation
            break
        }
    }
}
```

Differences from Senior 1:

-   Use of a third-party WebSocket library (Starscream) to handle the low-level
    details of establishing and managing the WebSocket connection, rather than
    implementing everything from scratch.
-   Better error handling, including handling specific error cases and
    gracefully disconnecting from the server when the session is finished.
-   Implementation of the **`WebSocketDelegate`** protocol to handle incoming
    and outgoing messages, rather than directly handling the socket
    communication within the **`VideoChatSession`** class.

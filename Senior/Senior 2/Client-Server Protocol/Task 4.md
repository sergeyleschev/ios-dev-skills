# Task 4

Task: Implement a real-time chat application using WebSocket protocol to
communicate between the client and server. The app should have a login screen to
authenticate users, a list of active chat rooms, and a chat view where users can
exchange text messages in real-time. The app should be able to handle multiple
chat rooms and multiple users in each chat room. Use URLSession for WebSocket
communication.

Solution: To implement the real-time chat application using WebSocket protocol,
we need to use the URLSessionWebSocketTask class provided by URLSession. Here's
a high-level overview of the steps involved:

1. Create a URLSession instance with default configuration.
2. Create a WebSocketTask with the desired URL.
3. Set the delegate for the WebSocketTask.
4. Connect to the WebSocket server using the resume() method.
5. Handle incoming messages in the didReceive method of the WebSocketTask's
   delegate.
6. Send outgoing messages using the send() method of the WebSocketTask.

Here's a code snippet that shows the implementation of the WebSocketTask and the
URLSession:

```swift
class WebSocketManager: NSObject {
    var socketTask: URLSessionWebSocketTask!
    var delegate: WebSocketManagerDelegate?

    func connect() {
        let url = URL(string: "wss://example.com/chat")!
        let session = URLSession(configuration: .default)
        socketTask = session.webSocketTask(with: url)
        socketTask.resume()
        receiveMessage()
    }

    func sendMessage(_ message: String) {
        let message = URLSessionWebSocketTask.Message.string(message)
        socketTask.send(message) { error in
            if let error = error {
                print("Error sending message: \(error)")
            }
        }
    }

    private func receiveMessage() {
        socketTask.receive { result in
            switch result {
            case .success(let message):
                switch message {
                case .string(let text):
                    self.delegate?.didReceiveMessage(text)
                case .data(let data):
                    print("Received data: \(data)")
                @unknown default:
                    print("Unknown message type received")
                }
                self.receiveMessage()
            case .failure(let error):
                print("Error receiving message: \(error)")
            }
        }
    }
}

protocol WebSocketManagerDelegate {
    func didReceiveMessage(_ message: String)
}
```

This code creates a WebSocketManager class that handles the WebSocket
communication with the server. The connect() method sets up the WebSocketTask
and starts listening for incoming messages. The sendMessage() method sends
outgoing messages to the server. The receiveMessage() method handles incoming
messages and passes them to the WebSocketManagerDelegate for further processing.
The delegate should be set by the view controller that uses the
WebSocketManager.

To implement the login screen, we can use a simple form that asks the user for
their username and password. We can then send the credentials to the server
using a regular HTTP POST request. If the server validates the credentials, it
can return an access token that the app can use for subsequent WebSocket
communication.

To implement the chat room list and chat view, we can use UITableView and
UICollectionView to display the list of active chat rooms and the messages in
each chat room. We can use the WebSocketManager to send and receive messages in
real-time.

One key difference between a Senior 1 and a Senior 2 developer is their ability
to handle complex networking scenarios. A Senior 2 developer should be able to
handle scenarios such as offline mode, slow network connections, and error
handling more effectively than a Senior 1 developer. They should also have a
deeper understanding of network protocols and security.

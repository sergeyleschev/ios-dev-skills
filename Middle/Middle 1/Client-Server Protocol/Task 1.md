# Task 1

Task: Build a real-time chat app using WebSocket and implement basic
authentication for users.

Solution: First, we need to establish a WebSocket connection with the server. We
can use the **`WebSocket`** class from the **`Starscream`** library to achieve
this.

```swift
import Starscream

let socket = WebSocket(url: URL(string: "ws://localhost:8080")!)
socket.connect()
```

Next, we need to implement authentication for users. We can do this by sending
the user's credentials to the server in a JSON format.

```swift
let credentials = ["username": "user1", "password": "password1"]
let json = try? JSONSerialization.data(withJSONObject: credentials, options: [])
socket.write(data: json!)
```

On the server-side, we can authenticate the user by verifying their credentials
and sending a response back to the client.

Once the user is authenticated, they can start sending and receiving messages
using the WebSocket connection.

To send a message, we can use the **`write(string:)`** method of the
**`WebSocket`** class.

```swift
let message = ["from": "user1", "to": "user2", "text": "Hello, user2!"]
let json = try? JSONSerialization.data(withJSONObject: message, options: [])
socket.write(data: json!)
```

To receive messages, we can implement the **`didReceiveMessage`** delegate
method of the **`WebSocketDelegate`** protocol.

```swift
func websocketDidReceiveMessage(socket: WebSocketClient, text: String) {
    let message = try? JSONSerialization.jsonObject(with: text.data(using: .utf8)!, options: []) as? [String: String]
    print("Received message from \(message?["from"] ?? ""): \(message?["text"] ?? "")")
}
```

The main difference between a junior 3 and a middle 1 developer in this task
would be the complexity and scalability of the implementation. A middle 1
developer would need to consider factors such as server load, error handling,
and message persistence. They may also need to implement more advanced features
such as group chat and push notifications.

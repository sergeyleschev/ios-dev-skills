# Task 4

Task: Create a real-time chat app using WebSocket protocol. The app should allow
users to join a chat room, send messages, and receive messages in real-time. Use
the Starscream library for handling WebSocket connections.

Solution: To create a WebSocket-based real-time chat app, we can follow these
steps:

1. Install Starscream using CocoaPods by adding the following line to the
   Podfile:

```ruby
pod 'Starscream'
```

2. In the view controller where the chat UI will be displayed, import Starscream
   and create a WebSocket object:

```swift
import Starscream

class ChatViewController: UIViewController {
    var socket: WebSocket?

    override func viewDidLoad() {
        super.viewDidLoad()

        // Initialize the WebSocket object
        socket = WebSocket(url: URL(string: "wss://chat-server.com")!)
    }

    // Rest of the code for the chat UI
}
```

3. Implement the WebSocketDelegate protocol in the view controller:

```swift
class ChatViewController: UIViewController, WebSocketDelegate {
    // ...

    override func viewDidLoad() {
        super.viewDidLoad()

        socket?.delegate = self
    }

    func websocketDidConnect(socket: WebSocketClient) {
        // Called when the WebSocket connection is established
        print("WebSocket connected")
    }

    func websocketDidDisconnect(socket: WebSocketClient, error: Error?) {
        // Called when the WebSocket connection is disconnected
        print("WebSocket disconnected: \(error?.localizedDescription ?? "")")
    }

    func websocketDidReceiveMessage(socket: WebSocketClient, text: String) {
        // Called when a message is received from the WebSocket server
        print("Received message: \(text)")
    }

    func websocketDidReceiveData(socket: WebSocketClient, data: Data) {
        // Called when binary data is received from the WebSocket server
    }

    // ...
}
```

4. Connect to the WebSocket server when the view appears:

```swift
class ChatViewController: UIViewController, WebSocketDelegate {
    // ...

    override func viewDidAppear(_ animated: Bool) {
        super.viewDidAppear(animated)

        socket?.connect()
    }

    // ...
}
```

5. Join the chat room when the user enters their name and taps the "Join"
   button:

```swift
class ChatViewController: UIViewController, WebSocketDelegate {
    // ...

    @IBOutlet weak var nameTextField: UITextField!

    @IBAction func joinButtonTapped(_ sender: UIButton) {
        guard let name = nameTextField.text else {
            return
        }

        let message = "join:\(name)"
        socket?.write(string: message)
    }

    // ...
}
```

6. Send a message when the user types a message and taps the "Send" button:

```swift
class ChatViewController: UIViewController, WebSocketDelegate {
    // ...

    @IBOutlet weak var messageTextField: UITextField!

    @IBAction func sendButtonTapped(_ sender: UIButton) {
        guard let message = messageTextField.text else {
            return
        }

        socket?.write(string: message)
    }

    // ...
}
```

7. Disconnect from the WebSocket server when the view disappears:

```swift
class ChatViewController: UIViewController, WebSocketDelegate {
    // ...

    override func viewDidDisappear(_ animated: Bool) {
        super.viewDidDisappear(animated)

        socket?.disconnect()
    }

    // ...
}
```

With these steps, we have a basic real-time chat app using WebSocket protocol.
To take this app to the next level, we could add features like message history,
user authentication, and more.

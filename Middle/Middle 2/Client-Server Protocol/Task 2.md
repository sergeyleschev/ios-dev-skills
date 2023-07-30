# Task 2

Task:

You are building a real-time chat app that uses WebSockets to communicate with
the server. The app should allow users to join different chat rooms, send and
receive messages, and receive real-time updates when new messages arrive.

As a Middle (2 of 3) iOS developer, your task is to implement the logic to
handle real-time updates from the server and display them in the app.
Specifically, you need to:

1. Set up a WebSocket connection to the server when the user enters a chat room.
2. Receive and parse real-time updates (in JSON format) from the server.
3. Update the app UI to display new messages in real-time.

Solution:

1. Set up a WebSocket connection to the server when the user enters a chat room:

```swift
import Starscream // assuming Starscream library is used for WebSockets

let socket = WebSocket(url: URL(string: "wss://your.server.com/chat")!)
socket.connect()
```

2. Receive and parse real-time updates (in JSON format) from the server:

```swift
socket.onText = { [weak self] text in
    guard let data = text.data(using: .utf8),
          let message = try? JSONDecoder().decode(Message.self, from: data)
    else { return }
    self?.receivedMessage(message)
}
```

Here, **`Message`** is a Codable struct that represents the data structure of a
chat message. The **`receivedMessage`** method is a function that takes a
**`Message`** object as input and updates the app UI to display the new message.

3. Update the app UI to display new messages in real-time:

```swift
func receivedMessage(_ message: Message) {
    // Add the new message to the chat history
    chatHistory.append(message)

    // Reload the table view to display the new message
    tableView.reloadData()

    // Scroll to the bottom of the table view to show the latest message
    tableView.scrollToRow(at: IndexPath(row: chatHistory.count - 1, section: 0), at: .bottom, animated: true)
}
```

Here, **`chatHistory`** is an array of **`Message`** objects that represents the
chat history, and **`tableView`** is a **`UITableView`** that displays the chat
messages. The **`receivedMessage`** method adds the new message to the
**`chatHistory`** array, reloads the table view to display the new message, and
scrolls to the bottom of the table view to show the latest message.

Differences from Middle 1 level: At Middle 2 level, the developer is expected to
have a deeper understanding of real-time communication protocols and how to
handle real-time updates from the server. They should also be familiar with
third-party libraries and frameworks that can simplify the implementation of
real-time chat functionality. Additionally, they should have a good
understanding of how to update the app UI in real-time and handle asynchronous
events.

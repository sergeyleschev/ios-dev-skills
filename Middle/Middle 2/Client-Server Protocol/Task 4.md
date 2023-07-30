# Task 4

Task: Write a function that retrieves the last 10 messages from a
WebSocket-based chat server and displays them in a UITableView. Each cell in the
table view should display the message text, the sender's username, and the
timestamp.

Solution:

```swift
class ChatViewController: UIViewController {

    @IBOutlet weak var tableView: UITableView!

    var chatMessages: [ChatMessage] = []

    override func viewDidLoad() {
        super.viewDidLoad()

        // Set up table view
        tableView.delegate = self
        tableView.dataSource = self

        // Connect to WebSocket server and retrieve last 10 messages
        let webSocket = WebSocket(url: URL(string: "ws://example.com/chat")!)
        webSocket.connect()
        webSocket.onText = { [weak self] text in
            guard let data = text.data(using: .utf8),
                  let message = try? JSONDecoder().decode(ChatMessage.self, from: data) else {
                return
            }
            self?.chatMessages.append(message)
            self?.tableView.reloadData()
        }
        webSocket.onConnect = {
            webSocket.send("get_last_10_messages")
        }
    }
}

extension ChatViewController: UITableViewDelegate, UITableViewDataSource {

    func tableView(_ tableView: UITableView, numberOfRowsInSection section: Int) -> Int {
        return chatMessages.count
    }

    func tableView(_ tableView: UITableView, cellForRowAt indexPath: IndexPath) -> UITableViewCell {
        let cell = tableView.dequeueReusableCell(withIdentifier: "ChatCell", for: indexPath) as! ChatCell
        let message = chatMessages[indexPath.row]
        cell.configure(with: message)
        return cell
    }
}

class ChatCell: UITableViewCell {

    @IBOutlet weak var messageLabel: UILabel!
    @IBOutlet weak var senderLabel: UILabel!
    @IBOutlet weak var timestampLabel: UILabel!

    func configure(with message: ChatMessage) {
        messageLabel.text = message.text
        senderLabel.text = message.sender
        timestampLabel.text = message.timestamp
    }
}

struct ChatMessage: Decodable {
    let text: String
    let sender: String
    let timestamp: String
}
```

The key difference between this task and the previous one is that it involves
retrieving data from a WebSocket server and displaying it in a table view. This
requires knowledge of asynchronous programming, data modeling, and table view
management. To solve this task, the developer needs to know how to set up a
WebSocket connection, handle incoming data, parse JSON data into a Swift data
model, and update the table view. The use of a separate cell class also
demonstrates a knowledge of encapsulation and reuse. Overall, this task is more
complex than the previous one and requires a higher level of skill in iOS
development.

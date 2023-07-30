# Task 1

Task: Implement a reconnection mechanism for the WebSocket connection in a
real-time chat application, which automatically reconnects the WebSocket if the
connection is lost due to network issues.

Solution:

To implement a reconnection mechanism for the WebSocket connection, we need to
keep track of the WebSocket connection state and try to reconnect if the
connection is lost due to network issues. Here's how we can do it:

```swift
class WebSocketManager {

    private var webSocketTask: URLSessionWebSocketTask?
    private var urlSession: URLSession?
    private var reconnectTimer: Timer?
    private var isConnected = false

    func connect() {
        guard let url = URL(string: "wss://example.com/chat") else { return }
        let request = URLRequest(url: url)
        urlSession = URLSession(configuration: .default, delegate: self, delegateQueue: nil)
        webSocketTask = urlSession?.webSocketTask(with: request)
        webSocketTask?.resume()
        receive()
    }

    func disconnect() {
        webSocketTask?.cancel(with: .normalClosure, reason: nil)
        isConnected = false
        stopReconnectTimer()
    }

    private func receive() {
        webSocketTask?.receive { [weak self] result in
            guard let self = self else { return }
            switch result {
            case .success(let message):
                // handle received message
                self.receive()
            case .failure(let error):
                print("WebSocket receive error: \(error.localizedDescription)")
                self.isConnected = false
                self.startReconnectTimer()
            }
        }
    }

    private func startReconnectTimer() {
        guard reconnectTimer == nil else { return }
        reconnectTimer = Timer.scheduledTimer(withTimeInterval: 5, repeats: true) { [weak self] _ in
            guard let self = self else { return }
            if !self.isConnected {
                self.connect()
            }
        }
    }

    private func stopReconnectTimer() {
        reconnectTimer?.invalidate()
        reconnectTimer = nil
    }
}

extension WebSocketManager: URLSessionWebSocketDelegate {

    func urlSession(_ session: URLSession, webSocketTask: URLSessionWebSocketTask, didOpenWithProtocol protocol: String?) {
        isConnected = true
        stopReconnectTimer()
    }

    func urlSession(_ session: URLSession, task: URLSessionTask, didCompleteWithError error: Error?) {
        print("WebSocket task error: \(error?.localizedDescription ?? "unknown error")")
        isConnected = false
        startReconnectTimer()
    }

}
```

In this implementation, we have added a **`reconnectTimer`** property, which is
started when the WebSocket connection is lost due to a network error. The timer
tries to reconnect to the server every 5 seconds until the connection is
re-established. Once the connection is re-established, the timer is stopped. The
**`stopReconnectTimer()`** method is called when the connection is disconnected
manually by calling **`disconnect()`**.

The main difference between this solution and the one provided for the previous
level is the addition of the reconnect mechanism. This requires the developer to
have a good understanding of WebSocket protocols, network communication, and
error handling. Additionally, the code should be well-structured and
maintainable, with a clear separation of concerns between the WebSocketManager
and URLSessionWebSocketDelegate.

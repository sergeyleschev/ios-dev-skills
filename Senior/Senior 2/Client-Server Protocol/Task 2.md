# Task 2

Task: Write a function that implements end-to-end encryption for messages in a
chat app. The function should take in a message string and return the encrypted
message string. Use the AES encryption algorithm and a 256-bit encryption key.

Solution:

```swift
import CryptoKit

func encryptMessage(_ message: String, withKey key: SymmetricKey) -> String? {
    guard let messageData = message.data(using: .utf8) else {
        return nil
    }

    let sealedBox = try? AES.GCM.seal(messageData, using: key)
    let encryptedData = sealedBox?.combined
    let encryptedString = encryptedData?.base64EncodedString()

    return encryptedString
}

// Example usage
let message = "Hello world!"
let key = SymmetricKey(size: .bits256)

if let encryptedMessage = encryptMessage(message, withKey: key) {
    print("Encrypted message: \(encryptedMessage)")
}
```

This task demonstrates the ability to implement end-to-end encryption using a
well-established encryption algorithm. It also shows a solid understanding of
working with encryption keys and converting between different data types. A
senior 2 developer should be able to implement this solution efficiently and
securely.

# Task 1

## **Task: Implement a Notification Service**

You need to implement a notification service that notifies the user whenever a
new message arrives in the app. The notification should be displayed as a banner
at the top of the screen and should disappear after a few seconds.

The notification service should use the Observer pattern to notify the view
controller about the new message.

### **Requirements:**

-   You need to create a **`NotificationService`** class that handles
    notifications.
-   The **`NotificationService`** class should have a method to add an observer.
-   The **`NotificationService`** class should have a method to remove an
    observer.
-   The **`NotificationService`** class should have a method to notify the
    observer about the new message.
-   The **`NotificationService`** class should handle the display of the
    notification banner.
-   The view controller should be able to add and remove itself as an observer
    of the **`NotificationService`**.
-   The view controller should be notified when a new message arrives.
-   The notification banner should disappear after a few seconds.

### **Constraints:**

-   You cannot use third-party libraries.
-   You cannot use Storyboards or SwiftUI.

### **Example Solution:**

```swift
protocol NotificationObserver: AnyObject {
    func handleNewMessage()
}

class NotificationService {
    private var observers = [NotificationObserver]()

    func addObserver(_ observer: NotificationObserver) {
        observers.append(observer)
    }

    func removeObserver(_ observer: NotificationObserver) {
        observers.removeAll(where: { $0 === observer })
    }

    func notifyObservers() {
        for observer in observers {
            observer.handleNewMessage()
        }
    }

    func showNotification() {
        // Display notification banner
    }
}

class ViewController: UIViewController {
    private let notificationService = NotificationService()

    override func viewDidLoad() {
        super.viewDidLoad()
        notificationService.addObserver(self)
    }

    func handleNewMessage() {
        notificationService.showNotification()
    }

    deinit {
        notificationService.removeObserver(self)
    }
}
```

In this solution, we have created a **`NotificationService`** class that handles
the notifications. The **`NotificationService`** class has methods to add and
remove observers, notify observers about new messages, and handle the display of
the notification banner.

We have also created a **`NotificationObserver`** protocol that the view
controller adopts to handle the new message notification. The
**`ViewController`** adds itself as an observer of the **`NotificationService`**
in its **`viewDidLoad()`** method and removes itself in the **`deinit()`**
method to avoid memory leaks.

When a new message arrives, the **`NotificationService`** calls the
**`handleNewMessage()`** method on all observers, which triggers the display of
the notification banner in the view controller.

# Task 3

Task: Write a function that checks if the app can make network requests.

Solution:

```swift
func canMakeNetworkRequests() -> Bool {
    let reachability = try? Reachability()
    return reachability?.connection != .unavailable
}
```

Explanation:

This function uses the **`Reachability`** class to check if the device has an
available network connection. The **`try?`** keyword is used to safely
initialize an instance of **`Reachability`**. If the initialization is
successful, the function checks the **`connection`** property of the
**`Reachability`** instance to see if it is not **`.unavailable`**. If the
connection is available, the function returns **`true`**, indicating that the
app can make network requests, and **`false`** otherwise.

Example usage:

```swift
if canMakeNetworkRequests() {
    print("App can make network requests")
} else {
    print("App cannot make network requests")
}
```

This function is a simple way to test if the app has network connectivity, which
is a common requirement for many apps that rely on network requests.

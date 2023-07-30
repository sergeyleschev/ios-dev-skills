# Task 1

Task: Write a function that checks if the app is running on the device with a
specific phone model.

Solution:

```swift
func isRunningOnDevice(model: String) -> Bool {
    let deviceModel = UIDevice.current.model
    return deviceModel == model
}
```

Explanation:

This function takes a phone model as a parameter and checks if the current
device model matches it. It uses the **`UIDevice.current.model`** property to
get the current device model and compares it with the model parameter. It
returns **`true`** if the models match, indicating that the app is running on
the specified device model, and **`false`** otherwise.

Example usage:

```swift
if isRunningOnDevice(model: "iPhone 12") {
    print("App is running on an iPhone 12")
} else {
    print("App is not running on an iPhone 12")
}
```

This function is a simple way to test if the app is working on a specific phone
model, which is a common requirement for quality assurance.

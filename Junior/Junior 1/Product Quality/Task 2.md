# Task 2

Task: Write a function that checks if the app has permission to access the
device's camera.

Solution:

```swift
func hasCameraPermission() -> Bool {
    return AVCaptureDevice.authorizationStatus(for: .video) == .authorized
}
```

Explanation:

This function checks if the app has permission to access the device's camera by
using the **`AVCaptureDevice.authorizationStatus(for:)`** method with
**`.video`** parameter, which returns the current authorization status for the
video media type. It then compares the authorization status with the
**`.authorized`** case to check if the app has permission to access the camera.
If the authorization status is **`.authorized`**, the function returns
**`true`**, indicating that the app has permission to access the camera, and
**`false`** otherwise.

Example usage:

```swift
if hasCameraPermission() {
    print("App has permission to access the camera")
} else {
    print("App does not have permission to access the camera")
}
```

This function is a simple way to test if the app has permission to access the
device's camera, which is a common requirement for many camera-related apps.

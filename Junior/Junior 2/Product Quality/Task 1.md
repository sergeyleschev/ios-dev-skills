# Task 1

Task: Write a function that checks if the app has access to the device's photo
library.

Solution:

```swift
func hasPhotoLibraryAccess() -> Bool {
    let status = PHPhotoLibrary.authorizationStatus()
    return status == .authorized
}
```

Explanation:

This function uses the **`PHPhotoLibrary.authorizationStatus()`** method to
check if the app has permission to access the device's photo library. The method
returns the current authorization status for the photo library, which is
compared with the **`.authorized`** case to check if the app has permission to
access the photo library. If the authorization status is **`.authorized`**, the
function returns **`true`**, indicating that the app has permission to access
the photo library, and **`false`** otherwise.

Example usage:

```swift
if hasPhotoLibraryAccess() {
    print("App has permission to access the photo library")
} else {
    print("App does not have permission to access the photo library")
}
```

Difference between Junior 1 and Junior 2:

The Junior 2 level developer demonstrates an increased understanding of the
platform and frameworks by using a more specialized API like
**`PHPhotoLibrary`** rather than the more general **`UIDevice`** or
**`AVCaptureDevice`**. Additionally, the Junior 2 developer's solution is more
concise as it doesn't require the **`try?`** keyword to handle potential errors.
Furthermore, the Junior 2 developer's code demonstrates a better understanding
of Swift's optionals as they use the optional binding to unwrap the value of the
**`PHPhotoLibrary.authorizationStatus()`** method. Overall, the Junior 2
developer's solution is more advanced and concise than that of the Junior 1
developer.

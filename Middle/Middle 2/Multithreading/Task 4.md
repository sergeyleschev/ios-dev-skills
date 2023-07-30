# Task 4

Task:

You are working on a social media app that loads user profiles from a remote
server. The app fetches the user profile data using an API call and then
displays the profile information on the user's profile page. However, the API
call can sometimes take a long time to complete, which can cause the UI to
freeze. Write a code snippet that fetches the user profile data in a background
thread and then updates the UI with the profile information on the main thread.

Solution:

To fetch the user profile data in a background thread and update the UI with the
profile information on the main thread, we can use GCD to execute the API call
in a background thread with a lower quality of service (QoS) level. Once the API
call is complete, we can switch back to the main thread to update the UI with
the fetched data. Here's an example code snippet that demonstrates how to
achieve this:

```swift
DispatchQueue.global(qos: .background).async {
    // Fetch user profile data using API call
    let userProfileData = fetchUserProfileData()

    DispatchQueue.main.async {
        // Update the UI with the fetched profile data
        // For example, update the profile page with the fetched data
    }
}
```

In this code, we use the **`DispatchQueue.global(qos: .background).async`**
method to execute the API call in a background thread with a lower quality of
service (QoS) level. This ensures that the API call does not block the main
thread and cause the UI to freeze.

Once the API call is complete, we use **`DispatchQueue.main.async`** to switch
back to the main thread and update the UI with the fetched profile data. This
ensures that the UI updates are performed on the main thread, which is necessary
to avoid synchronization issues.

Difference from the Middle 1 level:

The code snippet above shows an understanding of how to use GCD to execute an
API call in a background thread with a lower quality of service (QoS) level and
then update the UI with the fetched data on the main thread. This demonstrates
an intermediate level of proficiency with multithreading concepts and a better
understanding of how to use GCD to handle long-running tasks that can
potentially block the UI. Additionally, an understanding of how to handle errors
and network failures can also be expected at this level.

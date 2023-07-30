# Task 5

Task: You're working on an app that has a feature that loads a large image into
a UIImageView. Your users are reporting that the app is becoming slow and
unresponsive after using this feature for a while. You suspect that there may be
a memory leak in your code related to the image loading. Identify the possible
causes of the issue and suggest a fix.

Solution: Possible causes of the issue could be that the app is not properly
managing the memory used by the image, leading to a buildup of memory usage over
time. One possible fix could be to use image resizing to reduce the size of the
image before loading it into the UIImageView, thereby reducing the amount of
memory used. Additionally, the image could be cached to reduce the amount of
time and memory used for subsequent loads. Finally, it's important to ensure
that any strong references to the UIImageView or the image itself are properly
managed and released when they are no longer needed.

# Task 1

Task: Design and implement a feature that allows users to send and receive
images in the chat module. The feature should support sending and receiving
multiple images, as well as showing previews of the images in the chat thread.
The images should be loaded asynchronously and cached for quick retrieval.

Solution: To implement this feature, we can use the existing chat module and add
support for sending and receiving images. We can create a new message type that
represents an image message, with fields for the image data and metadata (such
as file name and size). When a user selects an image to send, we can encode the
image data as a base64 string and include it in the message payload.

On the receiving end, we can check the message type and decode the base64 string
back into an image. We can then display the image in a preview cell in the chat
thread, along with any metadata (such as the file name). To support multiple
images, we can allow users to select multiple images to send at once, and we can
show multiple preview cells for incoming image messages.

To load and cache the images, we can use an image caching library like
SDWebImage. When a user sends an image, we can upload it to a cloud storage
service (such as AWS S3) and include the URL in the message payload. On the
receiving end, we can use the URL to download the image and cache it for quick
retrieval. We can also use SDWebImage to display the cached images in the
preview cells.

Difference from Middle 1: In this task, the developer needs to have a deeper
understanding of networking and caching, as well as experience with third-party
libraries. The developer needs to be able to design and implement a complex
feature with multiple moving parts, while also ensuring the feature is fast,
reliable, and user-friendly. The solution should also demonstrate a good
understanding of asynchronous programming and handling large data payloads (such
as images).

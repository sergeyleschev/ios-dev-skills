# Task 5

Task:

You have been tasked with integrating a new video chat feature into an existing
messaging app. This feature should allow users to start a video call with their
contacts while they are messaging each other.

As a Senior iOS Developer (level 2 of 2), your task is to come up with a design
and implementation plan for this feature that brings value from other platforms
and paradigms.

Solution:

For the video chat feature, I would recommend using the WebRTC (Web Real-Time
Communications) platform, which is open-source and designed for real-time
communications. This platform is available for iOS and is widely used for video
chat applications.

To integrate WebRTC into the messaging app, I would first design a new interface
that allows users to initiate a video call with their contacts. This interface
should be accessible from the chat view and allow users to switch between video
and audio calls seamlessly.

Next, I would create a signaling server that will be responsible for
establishing the connection between users. This server will allow the clients to
exchange metadata and initiate a video call. The server can be built using
Node.js or any other preferred server-side language.

After that, I would create a video call view that will be presented when the
video call is initiated. This view will allow users to see and hear each other,
and it will include controls for turning the microphone and camera on and off.

Finally, I would test the feature thoroughly to ensure that it works as expected
and meets all the requirements. I would also optimize the performance of the
feature to ensure that it works well on devices with different specifications
and network conditions.

By using the WebRTC platform and implementing a signaling server, we can bring
value from other platforms and paradigms, such as the web, and leverage existing
open-source solutions to implement this feature efficiently and effectively.
Additionally, the new interface and video call view will provide a seamless user
experience, making the messaging app more competitive in the market.

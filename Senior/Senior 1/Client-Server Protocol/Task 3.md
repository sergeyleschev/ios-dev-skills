# Task 3

Task: Implement a video chat feature in an existing iOS app using WebRTC. The
feature should support one-on-one video calls and allow users to switch between
the front and rear cameras during the call. The app should also be able to
handle connection interruptions and re-establish the connection automatically.

Solution:

To implement the video chat feature, we will use WebRTC, a popular open-source
technology that provides real-time communication capabilities between browsers
and mobile apps. Here are the steps to implement the feature:

1. Add the WebRTC library to the project using CocoaPods or Swift Package
   Manager.
2. Create a new view controller that will handle the video chat feature.
3. Configure the video chat view controller to handle the video call by setting
   up the WebRTC session, tracks, and signaling channel.
4. Implement the necessary methods for handling video and audio tracks, camera
   switching, and connection state changes.
5. Use a signaling server to establish a connection between the two users and
   exchange SDP (Session Description Protocol) messages.
6. Handle connection interruptions by monitoring the network status and
   re-establishing the connection automatically using ICE (Interactive
   Connectivity Establishment) protocols.

Differences between senior level and middle level:

At the senior level, the developer should have a deeper understanding of the
underlying protocols and technologies used in WebRTC, such as ICE, STUN, and
TURN servers. They should also be able to optimize the performance and
reliability of the video chat feature, such as reducing latency, improving video
quality, and handling different network conditions. In addition, the senior
developer should be able to design and implement a scalable architecture that
can handle multiple users and concurrent video calls. Finally, they should also
have strong debugging and troubleshooting skills to diagnose and fix complex
issues that may arise during the development and deployment of the feature.

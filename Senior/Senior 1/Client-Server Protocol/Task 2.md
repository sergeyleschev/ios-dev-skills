# Task 2

Task:

You are tasked with building a video chat feature in an iOS app. The feature
should allow users to make real-time video calls with each other. The app should
use a custom video codec to optimize video quality and minimize latency.
Additionally, the app should support group video calls with up to 4
participants.

Solution:

To implement the video chat feature, we will use WebRTC framework. WebRTC is a
free, open-source project that provides browsers and mobile applications with
Real-Time Communications (RTC) capabilities via simple APIs.

First, we will create a WebRTC peer connection using the **`RTCPeerConnection`**
class provided by WebRTC framework. We will use **`AVFoundation`** framework to
capture audio and video from the device's camera and microphone. We will then
use the **`RTCVideoSource`** and **`RTCAudioSource`** classes to create media
sources from the captured audio and video.

Next, we will create **`RTCMediaStream`** and add audio and video tracks to it
using the **`RTCVideoTrack`** and **`RTCAudioTrack`** classes. We will also
create a **`RTCVideoRenderer`** to render the video stream in the UI.

To establish a connection with another user, we will need to create a signaling
mechanism. We can use a WebSocket server to exchange signaling messages between
the two peers. Once the signaling process is complete, we can establish a direct
peer-to-peer connection between the two peers.

To support group video calls, we can use a mesh network topology. In this
topology, each peer connects to all the other peers in the group. We can use the
**`RTCMultiConnection`** class provided by WebRTC framework to manage the
connections between the peers.

To optimize video quality and minimize latency, we can use a custom video codec.
We can use the **`RTCVideoEncoderFactory`** and **`RTCVideoDecoderFactory`**
classes provided by WebRTC framework to create custom video encoder and decoder
implementations.

Some differences between a Senior (1 of 2) iOS Developer and a Middle (3 of 3)
iOS Developer may include:

1. Ability to architect and design complex systems: Senior developers have a
   deeper understanding of software architecture and design patterns. They can
   design complex systems that are scalable, maintainable, and efficient.
2. Experience with cross-functional collaboration: Senior developers have
   experience working with different teams such as product, design, and QA to
   deliver high-quality products. They can communicate effectively and
   collaborate with different stakeholders to achieve a common goal.
3. Mentoring and leadership skills: Senior developers can mentor and guide
   junior developers to help them grow and develop their skills. They can also
   provide technical leadership and help drive the technical direction of a
   project.

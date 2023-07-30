# Task 3

Task:

Create a Facade for a music player app that provides a simple interface for
playing music tracks. The Facade should have methods for starting, stopping, and
skipping to the next track, and should handle all the necessary details of
interacting with the underlying music player framework.

Solution:

```swift
import Foundation
import AVFoundation

class MusicPlayerFacade {

    private let player = AVQueuePlayer()
    private var playerItems = [AVPlayerItem]()

    func playTrack(url: URL) {
        let playerItem = AVPlayerItem(url: url)
        playerItems.append(playerItem)
        player.insert(playerItem, after: nil)
        player.play()
    }

    func stop() {
        player.pause()
        player.seek(to: .zero)
        playerItems.removeAll()
    }

    func skipToNextTrack() {
        player.advanceToNextItem()
    }
}
```

In this solution, we have created a **`MusicPlayerFacade`** class that provides
a simple interface for playing music tracks. The class uses the AVFoundation
framework to create an **`AVQueuePlayer`** and insert **`AVPlayerItem`**s to
play. The **`playTrack`** method takes a URL to a music track and creates a new
**`AVPlayerItem`** for it, which is then inserted into the queue and played. The
**`stop`** method pauses the player, seeks to the beginning, and removes all the
items from the queue. Finally, the **`skipToNextTrack`** method advances the
player to the next item in the queue.

Differences from Junior 3 level:

-   The solution requires knowledge of the Facade design pattern and how to use
    it to provide a simplified interface to a complex system.
-   The solution uses a third-party framework (AVFoundation) to implement the
    music player functionality, indicating a higher level of familiarity with
    external libraries and frameworks.
-   The code is more modular and structured, with clear separation of concerns
    between the Facade and the underlying music player implementation.

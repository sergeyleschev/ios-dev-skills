# Task 2

Task: Create a protocol called **`Playable`** with a method **`play()`**. Then
create a class called **`Song`** that conforms to **`Playable`** and has
properties **`title`** and **`artist`**. Finally, create an array of
**`Playable`** objects that includes at least one **`Song`**, and loop through
the array, calling the **`play()`** method on each object.

Solution:

```swift
protocol Playable {
    func play()
}

class Song: Playable {
    var title: String
    var artist: String

    init(title: String, artist: String) {
        self.title = title
        self.artist = artist
    }

    func play() {
        print("Playing \(title) by \(artist)")
    }
}

let song = Song(title: "Bohemian Rhapsody", artist: "Queen")
let playableObjects: [Playable] = [song]

for object in playableObjects {
    object.play()
}
```

Difference from Junior 1: The Junior 2 developer should be able to create and
use protocols, as demonstrated by the creation of the **`Playable`** protocol.
They should also be able to create classes that conform to protocols and
implement the required methods, as shown in the **`Song`** class. Additionally,
the Junior 2 developer should be able to create and use arrays of objects that
conform to protocols and call methods on those objects, as demonstrated by the
creation of the **`playableObjects`** array and the **`for`** loop that calls
the **`play()`** method on each object.

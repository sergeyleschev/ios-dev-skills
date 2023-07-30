# Task 3

Task: Create a thread-safe Singleton class called "DataManager" that can be
accessed from any thread in a multithreaded environment. The DataManager should
have a shared instance that can be accessed globally and it should have a method
"saveData(data: String)" that saves the provided data to a file on disk. The
DataManager should ensure that only one thread at a time is able to write to the
file to avoid data corruption.

Solution:

```swift
class DataManager {
    static let shared = DataManager()
    private let fileManager = FileManager.default
    private let dataFile = "data.txt"
    private let lock = NSLock()

    private init() {}

    func saveData(data: String) {
        lock.lock()
        defer {
            lock.unlock()
        }

        if let path = fileManager.urls(for: .documentDirectory, in: .userDomainMask).first?.appendingPathComponent(dataFile) {
            do {
                try data.write(to: path, atomically: true, encoding: .utf8)
            } catch {
                print("Error saving data: \(error.localizedDescription)")
            }
        }
    }
}
```

Differences that indicate a Senior level developer:

-   The use of a lock object to ensure thread safety when writing to the file
    indicates a solid understanding of thread synchronization and avoidance of
    race conditions.
-   The use of defer statement to ensure the lock is always unlocked, even if an
    error occurs while writing to the file, indicates a mastery of Swift
    language features and best practices.

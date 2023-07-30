# Task 1

Task: Write a function that asynchronously downloads and saves an image from a
URL, and returns the saved file URL. Handle potential errors such as invalid
URL, network errors, and file I/O errors.

Solution:

```swift
func downloadAndSaveImage(from url: URL, completion: @escaping (Result<URL, Error>) -> Void) {
    URLSession.shared.downloadTask(with: url) { (location, response, error) in
        if let error = error {
            completion(.failure(error))
            return
        }

        guard let httpResponse = response as? HTTPURLResponse,
              (200...299).contains(httpResponse.statusCode) else {
            completion(.failure(NetworkError.invalidResponse))
            return
        }

        guard let location = location else {
            completion(.failure(FileIOError.fileNotFound))
            return
        }

        let documentsDirectory = FileManager.default.urls(for: .documentDirectory, in: .userDomainMask)[0]
        let destinationURL = documentsDirectory.appendingPathComponent(url.lastPathComponent)

        do {
            try FileManager.default.moveItem(at: location, to: destinationURL)
            completion(.success(destinationURL))
        } catch {
            completion(.failure(error))
        }
    }.resume()
}
```

Differences from the middle level:

At the senior level, the candidate is expected to have a deeper understanding of
multithreading and concurrency problems beyond deadlocks, such as race
conditions and resource starvation. They should also be able to handle errors
more gracefully and write more robust code that takes into account potential
edge cases. In this example, we handle potential errors such as invalid URLs,
network errors, and file I/O errors, and we return a **`Result`** type to make
the API more explicit and easier to use.

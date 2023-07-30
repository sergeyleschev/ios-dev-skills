# Task 3

Task: Implement a Facade pattern to simplify the usage of multiple APIs for
weather forecast data. The Facade should provide a single method
**`fetchWeatherData(for city: String)`** that will fetch and parse the data from
multiple APIs, and return a unified WeatherData model.

Solution:

```swift
class WeatherDataFacade {
    private let api1: API1
    private let api2: API2
    private let api3: API3

    init(api1: API1, api2: API2, api3: API3) {
        self.api1 = api1
        self.api2 = api2
        self.api3 = api3
    }

    func fetchWeatherData(for city: String, completion: @escaping (Result<WeatherData, Error>) -> Void) {
        let group = DispatchGroup()
        var resultData: WeatherData?
        var resultError: Error?

        group.enter()
        api1.fetchWeatherData(for: city) { result in
            switch result {
            case .success(let data):
                resultData = data
            case .failure(let error):
                resultError = error
            }
            group.leave()
        }

        group.enter()
        api2.fetchWeatherData(for: city) { result in
            switch result {
            case .success(let data):
                resultData = data
            case .failure(let error):
                resultError = error
            }
            group.leave()
        }

        group.enter()
        api3.fetchWeatherData(for: city) { result in
            switch result {
            case .success(let data):
                resultData = data
            case .failure(let error):
                resultError = error
            }
            group.leave()
        }

        group.notify(queue: .main) {
            if let data = resultData {
                completion(.success(data))
            } else if let error = resultError {
                completion(.failure(error))
            } else {
                completion(.failure(APIError.unknown))
            }
        }
    }
}

struct WeatherData {
    let temperature: Double
    let description: String
    // other properties
}

enum APIError: Error {
    case unknown
}

protocol API1 {
    func fetchWeatherData(for city: String, completion: @escaping (Result<WeatherData, Error>) -> Void)
}

protocol API2 {
    func fetchWeatherData(for city: String, completion: @escaping (Result<WeatherData, Error>) -> Void)
}

protocol API3 {
    func fetchWeatherData(for city: String, completion: @escaping (Result<WeatherData, Error>) -> Void)
}
```

Differences that indicate the development of the developer to the level of
middle 3:

-   Proficient knowledge of Design Patterns, especially the Facade pattern.
-   Familiarity with using multiple APIs and integrating them into a single
    interface.
-   Strong understanding of asynchronous programming and using GCD to manage
    concurrent tasks.
-   Ability to handle errors and provide appropriate feedback to the user.
-   Short and concise code that follows best practices and is easy to read and
    maintain.

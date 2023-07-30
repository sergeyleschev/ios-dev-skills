# Task 1

Task: Implement Observer pattern for a weather app, where the user can subscribe
to different cities and get notified when the weather changes.

Solution:

```swift
// Define a protocol for observers
protocol WeatherObserver: AnyObject {
    func didUpdateWeather(_ weather: Weather, for city: String)
}

// Define a struct to represent weather data
struct Weather {
    let temperature: Double
    let conditions: String
}

// Define a class to represent the weather app
class WeatherApp {
    private var observers: [String: [WeatherObserver]] = [:]

    // Method to subscribe to a city's weather updates
    func subscribe(observer: WeatherObserver, for city: String) {
        if observers[city] == nil {
            observers[city] = []
        }
        observers[city]?.append(observer)
    }

    // Method to unsubscribe from a city's weather updates
    func unsubscribe(observer: WeatherObserver, from city: String) {
        observers[city]?.removeAll(where: { $0 === observer })
    }

    // Method to update the weather for a city and notify all subscribed observers
    func updateWeather(for city: String, with weather: Weather) {
        observers[city]?.forEach({ $0.didUpdateWeather(weather, for: city) })
    }
}

// Define a class to represent the weather display view
class WeatherDisplayView: WeatherObserver {
    private let city: String

    init(city: String) {
        self.city = city
    }

    func didUpdateWeather(_ weather: Weather, for city: String) {
        if self.city == city {
            print("The weather in \(city) is \(weather.temperature) degrees and \(weather.conditions).")
        }
    }
}

// Example usage:
let weatherApp = WeatherApp()
let londonView = WeatherDisplayView(city: "London")
let parisView = WeatherDisplayView(city: "Paris")

weatherApp.subscribe(observer: londonView, for: "London")
weatherApp.subscribe(observer: parisView, for: "Paris")

weatherApp.updateWeather(for: "London", with: Weather(temperature: 15, conditions: "sunny"))
weatherApp.updateWeather(for: "Paris", with: Weather(temperature: 10, conditions: "cloudy"))

weatherApp.unsubscribe(observer: parisView, from: "Paris")

weatherApp.updateWeather(for: "Paris", with: Weather(temperature: 8, conditions: "rainy"))
```

Differences from the previous level (Middle 2):

-   The implementation is more complex, involving multiple classes and
    protocols.
-   The solution includes a struct to represent the weather data, which was not
    present in the previous level.
-   The solution includes an explicit subscribe/unsubscribe mechanism for
    observers, which was not present in the previous level.
-   The solution demonstrates better use of Swift features such as optionals,
    closures, and protocols.

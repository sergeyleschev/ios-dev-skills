# Task 2

Task: Implement a simple weather app that uses the Observer design pattern to
notify the user when the temperature changes.

Solution: First, we create a Weather class that will hold the temperature value
and notify the observers when the temperature changes:

```swift
class Weather {
    var temperature: Double = 0 {
        didSet {
            notifyObservers()
        }
    }

    private var observers = [WeatherObserver]()

    func addObserver(_ observer: WeatherObserver) {
        observers.append(observer)
    }

    func removeObserver(_ observer: WeatherObserver) {
        if let index = observers.firstIndex(where: { $0 === observer }) {
            observers.remove(at: index)
        }
    }

    private func notifyObservers() {
        observers.forEach { observer in
            observer.temperatureDidChange(temperature)
        }
    }
}
```

Next, we create a protocol for the observers:

```swift
protocol WeatherObserver: AnyObject {
    func temperatureDidChange(_ temperature: Double)
}
```

Then, we create a ViewController that displays the temperature and conforms to
the WeatherObserver protocol:

```swift
class ViewController: UIViewController, WeatherObserver {
    private let weather = Weather()
    private let temperatureLabel = UILabel()

    override func viewDidLoad() {
        super.viewDidLoad()
        weather.addObserver(self)
        setupViews()
    }

    private func setupViews() {
        // Set up temperature label
        temperatureLabel.font = UIFont.systemFont(ofSize: 24)
        temperatureLabel.textAlignment = .center
        view.addSubview(temperatureLabel)
        temperatureLabel.translatesAutoresizingMaskIntoConstraints = false
        NSLayoutConstraint.activate([
            temperatureLabel.centerXAnchor.constraint(equalTo: view.centerXAnchor),
            temperatureLabel.centerYAnchor.constraint(equalTo: view.centerYAnchor)
        ])
    }

    func temperatureDidChange(_ temperature: Double) {
        temperatureLabel.text = "\(temperature)°C"
    }
}
```

Finally, we can update the temperature value in the Weather class and the
observer (ViewController) will be notified:

```swift
let weather = Weather()
let viewController = ViewController()

weather.temperature = 20.0 // Observer will display "20.0°C"
```

Differences from Junior 3 to Middle 1 level:

-   The task requires the use of the Observer design pattern, which is a more
    advanced and complex pattern than the previous levels.
-   The task involves implementing a simple app from scratch, rather than
    modifying an existing codebase.
-   The task requires more understanding of protocols, since the observer must
    conform to the WeatherObserver protocol.
-   The task involves creating and managing collections (arrays) of observers,
    which requires a deeper understanding of memory management in Swift.

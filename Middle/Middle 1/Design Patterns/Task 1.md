# Task 1

Task: Implement a basic weather app that displays the current temperature and
weather condition for a specific location. The app should use the Observer
design pattern to update the temperature and condition information in real-time.

Solution:

```swift
import UIKit

// Subject
class WeatherStation {
    var temperature: Int = 0 {
        didSet {
            notifyObservers()
        }
    }
    var condition: String = "" {
        didSet {
            notifyObservers()
        }
    }
    private var observers: [WeatherObserver] = []

    func addObserver(_ observer: WeatherObserver) {
        observers.append(observer)
    }

    func removeObserver(_ observer: WeatherObserver) {
        observers = observers.filter { $0 !== observer }
    }

    func notifyObservers() {
        observers.forEach { $0.update(temperature: temperature, condition: condition) }
    }
}

// Observer
protocol WeatherObserver: AnyObject {
    func update(temperature: Int, condition: String)
}

// ViewController
class WeatherViewController: UIViewController {

    let weatherStation = WeatherStation()
    var temperatureLabel: UILabel!
    var conditionLabel: UILabel!

    override func viewDidLoad() {
        super.viewDidLoad()

        temperatureLabel = UILabel()
        temperatureLabel.translatesAutoresizingMaskIntoConstraints = false
        view.addSubview(temperatureLabel)
        NSLayoutConstraint.activate([
            temperatureLabel.centerXAnchor.constraint(equalTo: view.centerXAnchor),
            temperatureLabel.centerYAnchor.constraint(equalTo: view.centerYAnchor, constant: -50)
        ])

        conditionLabel = UILabel()
        conditionLabel.translatesAutoresizingMaskIntoConstraints = false
        view.addSubview(conditionLabel)
        NSLayoutConstraint.activate([
            conditionLabel.centerXAnchor.constraint(equalTo: view.centerXAnchor),
            conditionLabel.topAnchor.constraint(equalTo: temperatureLabel.bottomAnchor, constant: 20)
        ])

        weatherStation.addObserver(self)
        update(temperature: weatherStation.temperature, condition: weatherStation.condition)
    }

    override func viewWillDisappear(_ animated: Bool) {
        super.viewWillDisappear(animated)

        weatherStation.removeObserver(self)
    }
}

extension WeatherViewController: WeatherObserver {
    func update(temperature: Int, condition: String) {
        temperatureLabel.text = "\(temperature)℃"
        conditionLabel.text = condition
    }
}
```

Differences between Middle 1 and Junior 3 level developers:

-   Middle 1 level developers should be proficient at understanding and
    implementing advanced design patterns, such as Observer.
-   They should have a better understanding of object-oriented programming
    concepts and be able to design and architect more complex applications.
-   They should be able to write more efficient and optimized code and have a
    better understanding of performance optimization techniques.
-   They should be able to work with more complex APIs and libraries and have a
    good understanding of software development best practices.

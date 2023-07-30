# Task 3

Task: Create a Facade pattern that simplifies the usage of CoreLocation
framework in your app. The Facade should include a method to request user
location permission, start updating the user location, and stop updating the
user location.

Solution:

```swift
import Foundation
import CoreLocation

class LocationFacade: NSObject {

    private let locationManager = CLLocationManager()
    var location: CLLocation?

    var authorizationStatus: CLAuthorizationStatus {
        return CLLocationManager.authorizationStatus()
    }

    override init() {
        super.init()
        locationManager.delegate = self
    }

    func requestAuthorization() {
        locationManager.requestWhenInUseAuthorization()
    }

    func startUpdatingLocation() {
        locationManager.startUpdatingLocation()
    }

    func stopUpdatingLocation() {
        locationManager.stopUpdatingLocation()
    }
}

extension LocationFacade: CLLocationManagerDelegate {
    func locationManager(_ manager: CLLocationManager, didUpdateLocations locations: [CLLocation]) {
        if let location = locations.last {
            self.location = location
        }
    }

    func locationManager(_ manager: CLLocationManager, didChangeAuthorization status: CLAuthorizationStatus) {
        if status == .authorizedWhenInUse {
            locationManager.startUpdatingLocation()
        }
    }
}
```

The differences that indicate the development of the developer to the level of
Middle 2 from the level of Middle 1 are:

1. More advanced understanding of the Facade design pattern and its applications
   in real-world scenarios.
2. Ability to handle more complex tasks that require integration with external
   frameworks and APIs.
3. Familiarity with CoreLocation framework and its functionality, as well as the
   ability to simplify its usage for other developers in the team.
4. Stronger understanding of Swift programming language, as demonstrated by the
   implementation of the LocationFacade class using advanced Swift features such
   as closures, optional binding, and protocol extensions.

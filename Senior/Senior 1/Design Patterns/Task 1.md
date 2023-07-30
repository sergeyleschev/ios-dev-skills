# Task 1

Task: Implement a simple iOS app that displays a list of photos retrieved from a
remote API. Use dependency injection to pass a photo service to the view
controller responsible for displaying the list.

Solution:

```swift
// PhotoService.swift

protocol PhotoService {
    func fetchPhotos(completion: @escaping ([Photo]?, Error?) -> Void)
}

class RemotePhotoService: PhotoService {
    func fetchPhotos(completion: @escaping ([Photo]?, Error?) -> Void) {
        // Implementation of fetching photos from remote API
    }
}

// PhotoListViewController.swift

class PhotoListViewController: UIViewController {

    private let photoService: PhotoService

    init(photoService: PhotoService) {
        self.photoService = photoService
        super.init(nibName: nil, bundle: nil)
    }

    required init?(coder: NSCoder) {
        fatalError("init(coder:) has not been implemented")
    }

    override func viewDidLoad() {
        super.viewDidLoad()
        // Call photoService to fetch photos and display them in the view
    }
}

// Dependency Injection in AppDelegate.swift

@UIApplicationMain
class AppDelegate: UIResponder, UIApplicationDelegate {

    func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {

        let window = UIWindow(frame: UIScreen.main.bounds)
        window.rootViewController = PhotoListViewController(photoService: RemotePhotoService())
        window.makeKeyAndVisible()

        return true
    }
}
```

Differences indicating development from Middle 3 to Senior 1:

1. Code organization and structure is more advanced, with clear separation of
   concerns and adherence to design patterns.
2. Use of protocols and interfaces to define contracts between components,
   enabling more flexibility and extensibility.
3. Use of dependency injection to promote decoupling and testability of
   components.
4. Implementation of error handling and asynchronous operations in a more robust
   and scalable manner.

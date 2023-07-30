# Task 2

Task: Implement a simple iOS app that displays a list of user posts retrieved
from a remote API. Use service locator pattern to obtain the instance of the API
client and pass it to the view controller responsible for displaying the list.

Solution:

```swift
// APIClient.swift

protocol APIClient {
    func fetchPosts(completion: @escaping ([Post]?, Error?) -> Void)
}

class RemoteAPIClient: APIClient {
    func fetchPosts(completion: @escaping ([Post]?, Error?) -> Void) {
        // Implementation of fetching posts from remote API
    }
}

// ServiceLocator.swift

class ServiceLocator {
    static let shared = ServiceLocator()

    private init() {}

    func getAPIClient() -> APIClient {
        return RemoteAPIClient()
    }
}

// PostListViewController.swift

class PostListViewController: UIViewController {

    private let apiClient: APIClient

    init() {
        self.apiClient = ServiceLocator.shared.getAPIClient()
        super.init(nibName: nil, bundle: nil)
    }

    required init?(coder: NSCoder) {
        fatalError("init(coder:) has not been implemented")
    }

    override func viewDidLoad() {
        super.viewDidLoad()
        // Call apiClient to fetch posts and display them in the view
    }
}

// AppDelegate.swift

@UIApplicationMain
class AppDelegate: UIResponder, UIApplicationDelegate {

    func application(_ application: UIApplication, didFinishLaunchingWithOptions launchOptions: [UIApplication.LaunchOptionsKey: Any]?) -> Bool {

        let window = UIWindow(frame: UIScreen.main.bounds)
        window.rootViewController = PostListViewController()
        window.makeKeyAndVisible()

        return true
    }
}
```

Differences indicating development from Middle 3 to Senior 1:

1. Use of the service locator pattern to manage the creation and retrieval of
   instances, promoting decoupling and extensibility.
2. Implementation of a shared singleton instance of the service locator to
   provide access to commonly used dependencies.
3. Use of default implementations and protocol extensions to provide common
   functionality across different implementations of the same interface.

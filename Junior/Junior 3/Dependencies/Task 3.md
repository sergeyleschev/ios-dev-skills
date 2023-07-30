# Task 3

Task:

As a Junior iOS Developer, you have been tasked with integrating a new
dependency into an existing project using CocoaPods. The dependency you need to
add is called "Alamofire", which is a popular networking library for iOS.

Your task is to add the Alamofire dependency to the project using CocoaPods and
make sure it's properly integrated. You should also create a simple network
request using Alamofire to test that it's working correctly.

Instructions:

1. Install CocoaPods (if you haven't already) using the terminal command
   **`sudo gem install cocoapods`**.
2. Navigate to the root directory of your project using the terminal.
3. Create a new file in the root directory of your project called "Podfile" by
   running the command **`touch Podfile`**.
4. Open the Podfile in a text editor and add the following lines:

```ruby
platform :ios, '12.0'
use_frameworks!

target 'YourProjectName' do
  pod 'Alamofire', '~> 5.4'
end
```

Replace **`YourProjectName`** with the actual name of your project.

5. Save the Podfile and close it.
6. Run the command **`pod install`** in the terminal to install the Alamofire
   dependency.
7. Open your Xcode project using the **`.xcworkspace`** file that was generated
   by CocoaPods.
8. Import Alamofire at the top of your Swift file:

```swift
import Alamofire
```

9. Create a simple network request using Alamofire by adding the following code
   to your Swift file:

```swift
AF.request("https://jsonplaceholder.typicode.com/posts").responseJSON { response in
    print(response)
}
```

10. Build and run your project to test that everything is working correctly.

---

Differences between Junior 2 and Junior 3:

For Junior 3, the interviewer should pay attention to the following differences:

1. Understanding of how to use CocoaPods: The Junior 3 candidate should be able
   to easily add a new dependency to an existing project using CocoaPods and
   understand how to manage dependencies in their project.
2. Knowledge of popular libraries: The Junior 3 candidate should be familiar
   with popular iOS libraries like Alamofire and know how to integrate them into
   a project.
3. Debugging skills: The Junior 3 candidate should be able to debug any issues
   that arise during the integration of a new dependency, such as fixing any
   build errors or resolving version conflicts.

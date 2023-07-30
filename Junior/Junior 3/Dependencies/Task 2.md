# Task 2

Task: You are working on an iOS project and want to use the popular networking
library Alamofire to handle your API calls. Add Alamofire as a dependency using
Cocoapods.

Solution:

1. Open Terminal on your Mac.
2. Navigate to your project's root directory using the 'cd' command.
3. Create a Podfile by typing 'touch Podfile' and press enter.
4. Open the Podfile using any text editor and add the following lines:

```ruby
platform :ios, '12.0'
target 'YourProjectName' do
  use_frameworks!
  pod 'Alamofire'
end
```

5. Save the Podfile and close the text editor.
6. In Terminal, type 'pod install' and press enter. This will install Alamofire
   and any other dependencies specified in your Podfile.
7. Wait for the installation to complete and then open your project's
   .xcworkspace file in Xcode.
8. In your code, import Alamofire and start using it to make API calls.

Differences from Junior 2 level: At the Junior 2 level, the developer was
expected to know how to use Cocoapods to add dependencies to their project. At
the Junior 3 level, the expectation is to know how to add specific dependencies
that are commonly used in iOS development, like Alamofire. Additionally, the
Junior 3 developer should be able to handle any issues that may arise during the
installation process, such as conflicts with other dependencies.

# Task 4

Task: Use a custom podspec file to install a dependency

Description: As a junior iOS developer, you should know how to use a custom
podspec file to install a dependency in your project using Cocoapods. In this
task, you will use a custom podspec file to install a dependency that is not
available in the public Cocoapods repository.

Steps:

1. Create a new directory in your project directory called "Podspecs".
2. Add your custom podspec file to the "Podspecs" directory.
3. Open the Podfile in your preferred text editor.
4. Add the following line to the top of the Podfile:

    source '**https://github.com/CocoaPods/Specs.git**' source './Podspecs'

5. Add the dependency to the Podfile using the following format:

    pod 'DependencyName', :podspec => 'Podspecs/CustomPodspec.podspec'

    Replace "DependencyName" with the name of the dependency and "CustomPodspec"
    with the name of your custom podspec file.

6. Save the Podfile and close the text editor.
7. Run the command "pod install" in the terminal to install the dependency using
   the custom podspec file.
8. Wait for the installation process to complete.
9. Open your project in Xcode and verify that the dependency has been added
   successfully.
10. Build and run your project to ensure that the new dependency is working
    correctly.

Expected outcome: The custom podspec file should be used to install the
dependency and the dependency should be added to the project successfully.

Time limit: 15 minutes.

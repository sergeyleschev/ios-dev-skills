# Task 3

Task: Remove a dependency using Cocoapods

Description: As a junior iOS developer, you should know how to remove a
dependency from an existing project using Cocoapods. In this task, you will
remove an existing dependency from your project.

Steps:

1. Open Terminal and navigate to the project directory.
2. Open the Podfile in your preferred text editor.
3. Find the line of the dependency you want to remove and comment it out using
   the "#" symbol at the beginning of the line.

    # **pod 'DependencyName', '~> VersionNumber'**

4. Save the Podfile and close the text editor.
5. Run the command "pod install" in the terminal to remove the dependency.
6. Wait for the removal process to complete.
7. Open your project in Xcode and verify that the dependency has been removed
   successfully.
8. Build and run your project to ensure that the removed dependency is no longer
   present.

Expected outcome: The dependency should be removed from the project and should
not appear in the Xcode project anymore.

Time limit: 15 minutes.

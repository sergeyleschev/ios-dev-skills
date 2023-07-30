# Task 2

Task: Update a dependency using Cocoapods

Description: As a junior iOS developer, you should know how to update a
dependency in an existing project using Cocoapods. In this task, you will update
an existing dependency to a newer version.

Steps:

1. Open Terminal and navigate to the project directory.
2. Run the command "pod outdated" to see which dependencies have newer versions
   available.
3. Identify the dependency you want to update and note its current version
   number.
4. Open the Podfile in your preferred text editor.
5. Update the version number of the dependency you want to update to the latest
   available version using the following format:

    pod 'DependencyName', '~> LatestVersionNumber'

    Replace "DependencyName" with the name of the dependency you want to update
    and "LatestVersionNumber" with the latest version available. You can find
    this information on the dependency's website or Github page.

6. Save the Podfile and close the text editor.
7. Run the command "pod update" in the terminal to update the dependency.
8. Wait for the update process to complete.
9. Open your project in Xcode and verify that the dependency has been updated
   successfully.
10. Build and run your project to ensure that the updated dependency is working
    correctly.

Expected outcome: The dependency should be updated to the latest version and
should work as expected.

Time limit: 15 minutes.

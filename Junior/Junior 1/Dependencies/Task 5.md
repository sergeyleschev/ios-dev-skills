# Task 5

Task: Update a dependency using Cocoapods

Description: As a junior iOS developer, you should know how to update a
dependency in an existing project using Cocoapods. In this task, you will update
an existing dependency in your project to the latest version.

Steps:

1. Open Terminal and navigate to the project directory.
2. Run the command "pod outdated" in the terminal to view the list of outdated
   dependencies in your project.
3. Identify the dependency you want to update and note down its name and version
   number.
4. Open the Podfile in your preferred text editor.
5. Find the line of the dependency you want to update and change the version
   number to "latest".

    pod 'DependencyName', :git =>
    '**https://github.com/DependencyName/DependencyName.git**', :tag => 'latest'

6. Save the Podfile and close the text editor.
7. Run the command "pod update" in the terminal to update the dependency to the
   latest version.
8. Wait for the update process to complete.
9. Open your project in Xcode and verify that the dependency has been updated
   successfully.
10. Build and run your project to ensure that the updated dependency is working
    correctly.

Expected outcome: The dependency should be updated to the latest version and
should be working correctly in the project.

Time limit: 15 minutes.

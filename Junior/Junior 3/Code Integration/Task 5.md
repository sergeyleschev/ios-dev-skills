# Task 5

Task:

You are working on a project with a team of developers, and you have been
assigned a new feature to implement. The feature involves creating a new view
controller that allows users to search for items and displays the search results
in a table view. You need to create a new branch in Git to work on this feature
and then merge it back into the main branch once you are done.

Write the commands you would use to:

1. Create a new branch called "search-feature".
2. Switch to the new branch.
3. Create a new view controller called "SearchViewController.swift".
4. Add the new file to the Xcode project.
5. Make some changes to the file and commit them.
6. Push the changes to the remote repository.
7. Merge the "search-feature" branch into the main branch.
8. Push the merged changes to the remote repository.

Solution:

1. **`git checkout -b search-feature`**
2. **`git checkout search-feature`**
3. **`touch SearchViewController.swift`**
4. Drag and drop the new file into Xcode project navigator or use the command
   line **`git add SearchViewController.swift`**
5. **`git commit -m "Created SearchViewController"`**
6. **`git push origin search-feature`**
7. **`git checkout main`** (switch to main branch)
8. **`git merge search-feature`**
9. **`git push origin main`**

---

The key difference between this task and the Junior 2 level task is the use of
branching and merging. Junior 3 level developers should be comfortable with
creating and managing branches in Git, as well as merging changes back into the
main branch. This task tests their ability to work on a new feature
independently and integrate their changes into the project.

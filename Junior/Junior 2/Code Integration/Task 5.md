# Task 5

Task: Your team is working on a project and you need to create a new branch for
a new feature that you will be working on. Create a new branch called
"new-feature" and switch to that branch. Make a change to an existing file
called "ViewController.swift" by adding a new method called
"newFeatureMethod()". Commit the change with the message "Added new feature
method". Push the branch to the remote repository.

Solution:

```bash
git checkout -b new-feature
// make the change to ViewController.swift by adding new method
git add ViewController.swift
git commit -m "Added new feature method"
git push origin new-feature
```

Differences from Junior 1:

-   The task requires the creation of a new branch, indicating familiarity with
    branching and version control.
-   The task requires pushing the branch to the remote repository, indicating
    knowledge of remote repositories and collaborating with a team.
-   The task requires a specific commit message, indicating an understanding of
    the importance of clear and descriptive commit messages.

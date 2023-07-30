# Task 4

Task:

Your team is working on a new feature for your iOS app and you've been tasked
with integrating the changes made by your teammates into the main branch using
Git.

1. Create a new branch called "feature-branch" and switch to it.
2. Merge the latest changes from the main branch into "feature-branch".
3. Resolve any merge conflicts.
4. Push the changes to the remote repository.
5. Create a pull request to merge "feature-branch" into the main branch.

Solution:

```bash
// Step 1: Create a new branch and switch to it
git checkout -b feature-branch

// Step 2: Merge latest changes from main branch
git merge main

// Step 3: Resolve merge conflicts (if any)
// Open the conflicted file in Xcode or any other text editor, resolve the conflicts, save and close the file.
// Then stage the resolved file:
git add <conflicted-file>

// After resolving all conflicts, commit the changes
git commit -m "Merged latest changes from main branch"

// Step 4: Push changes to remote repository
git push origin feature-branch

// Step 5: Create pull request to merge feature-branch into main branch
// Go to your Git repository in the web browser and create a pull request to merge feature-branch into main branch.
// Assign reviewers, provide a brief description of the changes made and click "Create Pull Request".
```

Differences from Junior level 3:

-   This task involves merging changes from the main branch into a feature
    branch, whereas the previous tasks involved creating and merging branches
    locally without a remote repository.
-   The task requires resolving merge conflicts, which is not required at the
    Junior level 3.
-   The task includes creating a pull request, which is a more formal and
    standard way of merging branches in a team environment.

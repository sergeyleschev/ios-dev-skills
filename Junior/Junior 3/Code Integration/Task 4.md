# Task 4

Task:

You are working on a team project and you need to merge your feature branch into
the main branch. However, you notice that the main branch has changed since you
last pulled it, and you need to resolve any conflicts before merging. Your task
is to:

1. Create a new branch off of the main branch called "feature-branch-merge"
2. Pull the latest changes from the main branch into your new feature branch
3. Resolve any conflicts that arise from the merge
4. Commit the changes and push the branch to the remote repository
5. Create a pull request from "feature-branch-merge" to "main" and request a
   code review from a team member

Solution:

```bash
# Step 1: Create new branch
$ git checkout -b feature-branch-merge main

# Step 2: Pull latest changes from main into new branch
$ git pull origin main

# Step 3: Resolve any conflicts that arise from the merge
# ...make necessary changes to resolve conflicts...

# Step 4: Commit changes and push branch to remote repository
$ git add .
$ git commit -m "Resolved conflicts and merged latest changes from main into feature-branch-merge"
$ git push -u origin feature-branch-merge

# Step 5: Create pull request and request code review
# ...create pull request from "feature-branch-merge" to "main" in your repository's web interface...
# ...request a code review from a team member...
```

Differences that indicate Junior 3 level:

-   Ability to handle more complex merge scenarios, including resolving
    conflicts.
-   Familiarity with creating and submitting pull requests for code review.
-   Understanding of the importance of code review and collaboration in team
    projects.

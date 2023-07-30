# Task 3

Task: Create a feature branch in Git, make changes to the code, and merge it
back into the main branch.

Instructions:

1. Create a new branch called "feature/new-feature"
2. Make changes to the code, such as adding a new button to the view controller.
3. Commit the changes with a meaningful commit message.
4. Push the changes to the feature branch.
5. Merge the changes from the feature branch back into the main branch.
6. Resolve any merge conflicts, if necessary.
7. Push the changes to the main branch.

Solution:

```bash
# Step 1: Create a new branch
git checkout -b feature/new-feature

# Step 2: Make changes to the code and commit the changes
# For example, add a new button to a view controller
git add .
git commit -m "Added new button to ViewController"

# Step 3: Push the changes to the feature branch
git push origin feature/new-feature

# Step 4: Merge the changes from the feature branch back into the main branch
git checkout main
git merge feature/new-feature

# Step 5: Resolve any merge conflicts
# If there are conflicts, resolve them and commit the changes
git add .
git commit -m "Resolved merge conflicts"

# Step 6: Push the changes to the main branch
git push origin main
```

Differences from Junior 2:

-   More advanced Git skills, such as creating and merging branches
-   Understanding of Git workflows and best practices
-   Ability to resolve merge conflicts

# Task 5

Task: Write a script that automates the process of merging a feature branch into
the main branch. The script should prompt the user for the feature branch name
and perform the following actions:

1. Switch to the main branch
2. Pull the latest changes from the remote main branch
3. Merge the feature branch into the main branch
4. Push the changes to the remote main branch

Solution:

```bash
bashCopy code
#!/bin/bash

echo "Enter the name of the feature branch you want to merge into main:"
read featureBranch

git checkout main
git pull origin main
git merge $featureBranch
git push origin main
```

Differences from Middle 1:

-   This task requires the developer to have a deeper understanding of git and
    how to automate common tasks.
-   The developer should be comfortable with writing shell scripts and be
    familiar with the basic syntax.
-   The developer should be able to understand and use git commands in
    combination to achieve a specific goal.

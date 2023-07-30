# Task 1

Task:

You are working on a project with your team and you have just received an email
from the project manager that there is a critical bug in the production app.
Your task is to fix the bug and deploy the changes to the production server
using git.

Solution:

1. Start by cloning the repository to your local machine:

```bash
git clone git@github.com:project/repo.git
```

2. Switch to the branch with the bug:

```bash
git checkout bugfix-branch
```

3. Make the necessary changes to fix the bug in the code.
4. Add the changes to the staging area:

```bash
git add .
```

5. Commit the changes:

```bash
git commit -m "Fixed the critical bug"
```

6. Push the changes to the remote branch:

```bash
git push origin bugfix-branch
```

7. Merge the changes with the production branch:

```bash
git checkout production-branch
git merge bugfix-branch
```

8. Push the changes to the production branch:

```bash
git push origin production-branch
```

9. Verify that the bug is fixed in the production environment.

Differences between Senior 1 and Middle 3:

-   Ability to quickly and effectively troubleshoot and fix production issues
-   Knowledge of advanced git commands such as merging and branching
-   Understanding of how to deploy changes to production servers
-   Stronger attention to detail and ability to write high-quality,
    well-documented code

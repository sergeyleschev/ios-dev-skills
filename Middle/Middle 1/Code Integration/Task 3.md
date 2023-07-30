# Task 3

Task:

You are working on a team project and need to merge your code changes with a
colleague's changes. Your colleague has pushed their changes to a feature branch
on the remote repository. Your task is to merge their changes into the local
master branch and resolve any conflicts that arise.

Solution:

1. Ensure that your local master branch is up to date with the remote
   repository:

```bash
git checkout master
git pull origin master
```

2. Create and checkout a new branch to merge the changes:

```bash
git checkout -b feature-branch-merge
```

3. Merge the feature branch changes into the new branch:

```bash
git merge origin/feature-branch
```

4. Resolve any conflicts that arise during the merge process:

```bash
<< resolve any conflicts >>
```

5. Commit the merged changes:

```bash
git add .
git commit -m "Merge feature-branch into master"
```

6. Push the merged changes to the remote repository:

```bash
git push origin feature-branch-merge
```

7. Create a pull request to merge the feature-branch-merge into the master
   branch on the remote repository.

Key differences from Junior 3:

-   The task involves merging changes from a remote feature branch, requiring
    knowledge of remote repositories and branching.
-   The task requires the developer to resolve conflicts that arise during the
    merge process, demonstrating an understanding of version control and code
    collaboration.
-   The developer is expected to create a new branch for the merge process,
    indicating an understanding of good Git practices for code integration.

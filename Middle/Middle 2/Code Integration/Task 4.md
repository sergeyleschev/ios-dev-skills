# Task 4

Task: You are working on a team developing a new feature for an app. Your team
has created a new branch in Git for this feature called "feature/new-feature".
Your task is to merge this branch into the "develop" branch and resolve any
conflicts that may arise.

Solution:

1. Fetch the latest changes from the remote repository:

```bash
git fetch
```

2. Switch to the "develop" branch:

```bash
git checkout develop
```

3. Merge the "feature/new-feature" branch into the "develop" branch:

```bash
git merge feature/new-feature
```

4. If any conflicts occur during the merge, resolve them by editing the affected
   files and then adding and committing the changes:

```bash
git add <conflicted-file>
git commit -m "Resolved merge conflict in <conflicted-file>"
```

5. Push the changes to the remote repository:

```bash
git push origin develop
```

Differences from Middle 1 level: In this task, the developer needs to have a
better understanding of Git and merging. They need to know how to resolve
conflicts that may arise during a merge and push the changes to the remote
repository. They also need to have a better understanding of Git branching and
be able to switch between different branches.

# Task 2

Task:

You are working on a project with a team of developers, and one of your team
members has created a new branch for a feature they are working on. However, the
feature branch has a few conflicts with the master branch, and your team member
needs your help resolving them. Your task is to merge the feature branch into
the master branch, resolving any conflicts that arise.

Technical requirements:

1. Use git to switch to the master branch.
2. Use git pull to ensure that your local master branch is up to date with the
   remote master branch.
3. Use git merge to merge the feature branch into the master branch.
4. Resolve any conflicts that arise during the merge.
5. Use git add to stage any changes resulting from the conflict resolution.
6. Use git commit to commit the merge changes to the master branch.

Solution:

1. Open the terminal and navigate to the project directory.
2. Enter the command **`git checkout master`** to switch to the master branch.
3. Enter the command **`git pull`** to ensure that your local master branch is
   up to date with the remote master branch.
4. Enter the command **`git merge <feature-branch-name>`** to merge the feature
   branch into the master branch.
5. Resolve any conflicts that arise during the merge by editing the affected
   files to remove the conflict markers and deciding which version of the code
   to keep.
6. Once all conflicts are resolved, use the command
   **`git add <resolved-file-names>`** to stage the changes resulting from the
   conflict resolution.
7. Use the command **`git commit -m "Merge feature branch into master"`** to
   commit the merge changes to the master branch with a meaningful commit
   message.
8. Push the updated master branch to the remote repository using the command
   **`git push`**.

Differences between Middle 2 and Middle 3 levels:

In this task, the developer is required to resolve conflicts that arise during
the merge. This requires a deeper understanding of git, version control, and
conflict resolution techniques. Additionally, the developer is required to write
a meaningful commit message that accurately describes the changes made during
the merge. These skills are indicative of a more experienced developer who is
comfortable working with complex codebases and collaborating with other
developers in a team environment.

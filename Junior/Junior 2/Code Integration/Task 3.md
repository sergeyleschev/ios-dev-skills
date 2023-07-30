# Task 3

Task: You are working on a team project and your team lead has assigned you to a
task to fix a bug in the code. You need to create a new branch for this task and
push the changes to the remote repository once the bug is fixed.

Solution:

1. Open the terminal and navigate to the local repository's directory.
2. Check if you are on the master branch by running **`git branch`** command.
3. If you are not on the master branch, switch to the master branch by running
   **`git checkout master`**.
4. Pull the latest changes from the remote repository by running
   **`git pull origin master`**.
5. Create a new branch for the bug fix by running **`git checkout -b bug-fix`**.
6. Make the necessary changes in the code to fix the bug.
7. Add the changes to the staging area by running **`git add .`**.
8. Commit the changes with a descriptive commit message by running
   **`git commit -m "Fixed the bug"`**
9. Push the changes to the remote repository by running
   **`git push origin bug-fix`**.
10. Once the changes are pushed, create a pull request for the bug fix branch
    and merge it with the master branch.

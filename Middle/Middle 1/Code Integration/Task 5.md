# Task 5

Task: You are working on a project with a team of developers, and you need to
add a new feature that involves making changes to the existing codebase. Create
a branch in Git, make the necessary changes to the code, and then merge the
changes back into the main branch.

Solution:

1. Navigate to the project's directory in your terminal and switch to the main
   branch by running the command **`git checkout main`**.
2. Create a new branch for your feature using the command
   **`git checkout -b feature/your-feature-name`**. This will create a new
   branch off of the main branch.
3. Make the necessary changes to the code in Xcode.
4. Once you are done making changes, stage the changes for commit using the
   command **`git add .`**.
5. Commit your changes using the command
   **`git commit -m "Add your commit message here"`**.
6. Push your changes to the remote repository using the command
   **`git push -u origin feature/your-feature-name`**. This will push your
   branch to the remote repository and set the upstream tracking branch to your
   local branch.
7. Once your changes have been pushed, create a pull request to merge your
   branch into the main branch. This can be done on the web interface of your
   Git hosting platform, such as GitHub or Bitbucket.
8. Have a teammate review your code changes and approve the pull request.
9. Merge your changes into the main branch using the web interface of your Git
   hosting platform or the command line with
   **`git merge feature/your-feature-name`**.
10. Finally, switch back to the main branch with **`git checkout main`** and
    delete the feature branch with
    **`git branch -d feature/your-feature-name`**.

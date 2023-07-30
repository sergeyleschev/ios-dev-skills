# Task 4

Task: You are working on a project with a team, and you need to create a new
branch from an existing branch to work on a new feature. You will need to create
the new branch, switch to it, and make changes to the codebase.

Solution:

1. Open the terminal and navigate to the project directory.
2. Use the following command to switch to the branch you want to create the new
   branch from:

    ```bash
    git checkout existing-branch-name
    ```

3. Use the following command to create a new branch from the existing branch:

    ```bash
    git branch new-branch-name
    ```

4. Use the following command to switch to the new branch:

    ```bash
    git checkout new-branch-name
    ```

5. Make changes to the codebase as needed.
6. Stage the changes using the following command:

    ```bash
    git add .
    ```

7. Commit the changes using the following command:Replace "Commit message" with
   a description of the changes you made.

    ```bash
    git commit -m "Commit message"
    ```

8. Push the changes to the new branch using the following command:

    ```bash
    git push origin new-branch-name
    ```

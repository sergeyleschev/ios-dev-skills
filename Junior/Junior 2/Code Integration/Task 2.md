# Task 2

Task: You have been tasked with merging a feature branch into the main branch.
Before doing so, you need to ensure that the feature branch is up to date with
the latest changes in the main branch, resolve any conflicts, and ensure that
the codebase remains stable and functional.

Solution:

1. Open the terminal and navigate to the project directory.
2. Switch to the main branch using the following command:

    ```bash
    git checkout main
    ```

3. Pull the latest changes from the main branch using the following command:

    ```bash
    git pull origin main
    ```

4. Switch to the feature branch using the following command:

    ```bash
    git checkout feature-branch
    ```

5. Merge the latest changes from the main branch into the feature branch using
   the following command:

    ```bash
    git merge main
    ```

6. Resolve any conflicts that arise during the merge process by editing the
   affected files in your text editor.
7. Test the codebase to ensure that it is stable and functional.
8. Stage the changes using the following command:

    ```bash
    git add .
    ```

9. Commit the changes using the following command:

    ```bash
    git commit -m "Merge main into feature-branch"
    ```

10. Push the changes to the feature branch using the following command:

    ```bash
    git push origin feature-branch
    ```

Difference between Junior 1 and Junior 2: Junior 2 developers should be able to
merge changes from one branch into another, resolve any conflicts that arise
during the merge process, and ensure that the codebase remains stable and
functional after the merge. They should also be able to test the codebase to
ensure that it is functional. Junior 2 developers have a deeper understanding of
Git and can perform more complex operations such as merging branches.

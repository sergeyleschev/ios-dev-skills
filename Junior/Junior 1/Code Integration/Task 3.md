# Task 3

Task: You are working on a project with a team, and you need to revert a commit
that was made in the main branch. You will need to identify the commit that
needs to be reverted and then revert it while preserving the rest of the commit
history.

Solution:

1. Open the terminal and navigate to the project directory.
2. Use the following command to view the commit history:

    ```bash
    git log
    ```

3. Identify the commit that needs to be reverted and copy its SHA-1 hash.
4. Use the following command to revert the commit:For example:

    ```bash
    git revert <commit-hash>
    ```

    ```bash
    git revert abcdef1234567890
    ```

5. If a merge conflict occurs during the revert, resolve it by reviewing the
   changes made in the conflicting files and determining how to merge them
   together.
6. Stage the changes using the following command:

    ```bash
    git add .
    ```

7. Commit the changes using the following command:For example:

    ```bash
    git commit -m "Reverted commit <commit-hash>"
    ```

    ```bash
    git commit -m "Reverted commit abcdef1234567890"
    ```

8. Push the changes to the main branch using the following command:

    ```bash
    git push origin main
    ```

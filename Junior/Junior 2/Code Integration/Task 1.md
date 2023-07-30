# Task 1

Task: You are working on a project with a team, and you need to revert a commit
that caused issues in the codebase. You will need to identify the commit and
revert it while preserving the integrity of the codebase.

Solution:

1. Open the terminal and navigate to the project directory.
2. Use the following command to view the commit history and identify the commit
   you want to revert:

    ```bash
    git log
    ```

3. Copy the commit hash of the commit you want to revert.
4. Use the following command to revert the commit:Replace COMMIT_HASH with the
   hash of the commit you want to revert.

    ```bash
    git revert COMMIT_HASH
    ```

5. Review the changes made by the revert in your text editor, and modify the
   code as needed to ensure that the codebase is stable and functional.
6. Stage the changes using the following command:

    ```bash
    git add .
    ```

7. Commit the changes using the following command:Replace COMMIT_HASH with the
   hash of the reverted commit.

    ```bash
    git commit -m "Revert COMMIT_HASH"
    ```

8. Push the changes to the branch using the following command:Replace
   BRANCH_NAME with the name of the branch you are working on.

    ```bash
    git push origin BRANCH_NAME
    ```

Difference between Junior 1 and Junior 2: Junior 2 developers should be able to
identify the commit causing issues in the codebase and revert it while ensuring
that the codebase remains stable and functional. They should also be able to
review the changes made by the revert and modify the code as needed to ensure
that it is functional. Junior 2 developers have a deeper understanding of Git
and can troubleshoot issues more effectively.

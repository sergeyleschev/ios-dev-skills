# Task 5

Task: You are working on a project with a team, and you need to resolve a merge
conflict that occurred when merging a feature branch into the main branch. You
will need to identify the conflicts and resolve them while preserving the
integrity of the codebase.

Solution:

1. Open the terminal and navigate to the project directory.
2. Use the following command to switch to the main branch:

    ```bash
    git checkout main
    ```

3. Use the following command to merge the feature branch into the main branch:

    ```bash
    git merge feature-branch
    ```

4. If there are conflicts, the terminal will display a message that the merge
   failed and that there are conflicts that need to be resolved. Use the
   following command to view the files with conflicts:

    ```bash
    git status
    ```

5. Open each file with conflicts in a text editor and review the changes made in
   the conflicting code sections. Determine how to merge the changes together,
   and then modify the code as needed to resolve the conflicts.
6. Once the conflicts have been resolved, stage the changes using the following
   command:

    ```bash
    git add .
    ```

7. Commit the changes using the following command:

    ```bash
    git commit -m "Resolved merge conflicts"
    ```

8. Push the changes to the main branch using the following command:

    ```bash
    git push origin main
    ```

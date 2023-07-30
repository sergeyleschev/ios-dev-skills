# Task 2

Task: You are working on a project with a team, and you need to resolve a merge
conflict that has occurred between two branches. You will need to review the
changes made in both branches and determine how to merge them together. Then,
you will need to resolve any conflicts and update the codebase.

Solution:

1. Open the terminal and navigate to the project directory.
2. Checkout the branch that you want to merge changes into using the following
   command:

    ```bash
    git checkout branch-name
    ```

3. Merge the other branch into the current branch using the following command:

    ```bash
    git merge other-branch-name
    ```

4. If a merge conflict occurs, you will need to resolve it by reviewing the
   changes made in both branches and determining how to merge them together.
5. Use the following command to view the conflicting files:

    ```bash
    git status
    ```

6. Open the conflicting file(s) in your code editor and review the changes made
   in both branches.
7. Determine how to merge the conflicting changes together and make the
   necessary edits to the file(s).
8. Stage the changes using the following command:

    ```bash
    git add .
    ```

9. Commit the changes using the following command:

    ```bash
    git commit -m "Resolved merge conflict"
    ```

10. Push the changes to the branch using the following command:

    ```bash
    git push origin branch-name
    ```

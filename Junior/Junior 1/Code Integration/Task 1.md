# Task 1

Task: You are working on a project with a team, and you need to integrate a new
feature into the codebase. You will need to create a new branch for the feature
and push your changes to that branch. Then, you will need to create a pull
request and have it reviewed by another member of the team before merging it
into the main branch. Finally, you will need to update your local copy of the
codebase to include the new changes.

Solution:

1. Open the terminal and navigate to the project directory.
2. Create a new branch for the feature using the following command:

    ```bash
    git checkout -b new-feature
    ```

3. Make the necessary changes to the codebase.
4. Stage the changes using the following command:

    ```bash
    git add .
    ```

5. Commit the changes using the following command:

    ```bash
    git commit -m "Implemented new feature"
    ```

6. Push the changes to the new branch using the following command:

    ```bash
    git push origin new-feature
    ```

7. Go to the GitHub repository and create a new pull request for the new branch.
8. Assign the pull request to another member of the team for review.
9. Once the pull request has been reviewed and approved, merge it into the main
   branch.
10. Update your local copy of the codebase to include the new changes using the
    following command:

    ```bash
    git pull origin main
    ```

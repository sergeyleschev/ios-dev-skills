# Task 1

Task:

You are working on a team that is building a new feature for an existing iOS
app. You have been assigned to implement a new view controller that displays
data from an API endpoint. Your task is to create a new branch in the project's
Git repository, implement the new view controller, and merge your changes back
into the main branch.

Solution:

1. First, create a new branch for your feature:
   **`git checkout -b feature/new-view-controller`**
2. Next, implement the new view controller, making sure to fetch the data from
   the API endpoint and display it in the appropriate format.
3. Once you are finished with your changes, commit them to your feature branch:
   **`git commit -m "Implement new view controller"`**
4. Push your changes to the remote repository:
   **`git push origin feature/new-view-controller`**
5. Create a pull request for your feature branch on the project's Git hosting
   platform (e.g. GitHub, GitLab, Bitbucket). Be sure to include a clear
   description of the changes you made and any relevant information for
   reviewers.
6. Once your pull request is approved, merge your changes into the main branch:
   **`git checkout maingit merge feature/new-view-controller`**
7. Push the merged changes to the remote repository: **`git push origin main`**

Differences from Middle 2 level:

At the Middle 3 level, the developer is expected to be able to handle more
complex branching and merging scenarios, such as dealing with conflicts between
branches, using advanced Git commands like rebase and cherry-pick, and
implementing a Git workflow for the team. Additionally, they should have a deep
understanding of Git concepts like branching, merging, and rebasing, and be able
to explain these concepts to others on the team.

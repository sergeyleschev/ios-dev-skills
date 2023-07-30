# Task 5

Task: Implement a Git branching strategy for a collaborative iOS project with
multiple developers. The strategy should include at least two main branches
(master and develop) and a feature branch workflow. Ensure that all developers
understand and follow the strategy.

Solution:

1. Create the master branch and push it to the remote repository.
2. Create the develop branch and push it to the remote repository.
3. Have all developers clone the repository.
4. Instruct developers to always branch off of the develop branch when starting
   work on a new feature.
5. Each developer should create a new branch for their feature, starting from
   the develop branch.
6. Developers should regularly pull changes from the develop branch to keep
   their feature branches up to date.
7. When a feature is complete, the developer should merge their feature branch
   into the develop branch and push the changes to the remote repository.
8. Only when a release is ready should the develop branch be merged into the
   master branch and pushed to the remote repository.
9. Instruct developers to delete their feature branches once they have been
   merged into the develop branch.

Differences that indicate development to the Middle 3 level from Middle 2 could
include:

-   Demonstrating an understanding of more advanced Git workflows, such as
    Gitflow or GitOps.
-   Showing an ability to resolve complex merge conflicts and properly merge
    branches.
-   Understanding how to use Git submodules or Git sub-trees to manage
    dependencies.
-   Demonstrating a deep understanding of Git best practices, such as how to
    write good commit messages and how to use Git to revert changes or view the
    history of a project.

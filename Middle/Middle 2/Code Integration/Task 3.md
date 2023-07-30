# Task 3

Task:

You are working on a project with a team, and you have just finished a new
feature. Before merging your changes to the main branch, you need to make sure
that your code passes all the tests and is reviewed by another developer. Your
team uses a Git workflow, and you are responsible for creating a pull request
for your changes.

Write a script that performs the following steps:

1. Checkout the main branch and pull the latest changes.
2. Create a new branch for your feature development.
3. Implement your new feature.
4. Run all the tests to ensure your code works as expected.
5. Commit your changes with a descriptive message.
6. Push your changes to your remote feature branch.
7. Create a pull request for your feature branch and assign it to a code
   reviewer.

Solution:

```bash
bashCopy code
#!/bin/bash

# Checkout main branch and pull latest changes
git checkout main
git pull

# Create new branch for feature development
git checkout -b new-feature

# Implement new feature
# ...

# Run tests
xcodebuild test -workspace MyProject.xcworkspace -scheme MyProjectTests -destination 'platform=iOS Simulator,name=iPhone 13'

# Commit changes
git add .
git commit -m "Implemented new feature"

# Push changes to remote branch
git push origin new-feature

# Create pull request and assign code reviewer
gh pr create --title "New feature" --body "Please review my new feature" --assignee @reviewer
```

Differences from Middle 1:

This task builds on the previous one by adding the steps of running tests and
creating a pull request for code review. At this level, a developer should be
comfortable with automated testing and Git workflows, including creating pull
requests and assigning reviewers. Additionally, the script now uses the **`gh`**
command-line tool to create the pull request, which is a more advanced tool than
simply using the Git command line.

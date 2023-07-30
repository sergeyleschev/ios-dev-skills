# Task 3

Task:

As a Senior iOS developer, you are responsible for creating a script that
automates the process of creating a release branch from the main branch. The
script should create a new branch with the name in the format "release/x.x.x",
where x.x.x is the version number of the release. The script should also update
the version number in the project's Info.plist file to match the release branch
name.

Solution:

```bash
#!/bin/bash

# Get current version number
version_number=$(grep -o '[0-9]\{1,\}\.[0-9]\{1,\}\.[0-9]\{1,\}' Info.plist)

# Create new release branch
release_branch_name="release/$version_number"
git checkout main
git pull
git checkout -b "$release_branch_name"

# Update Info.plist with new version number
sed -i '' "s/$version_number/$release_branch_name/g" Info.plist
git add Info.plist
git commit -m "Update version number for release $release_branch_name"

# Push branch to remote repository
git push -u origin "$release_branch_name"

echo "Release branch $release_branch_name has been created."
```

Differences indicating development to Senior 2:

-   Senior 2 developers are expected to have a deeper understanding of Git and
    its workflows, and are able to create complex scripts to automate tasks.
-   This task requires the use of shell scripting, which is not typically
    required at Senior 1 level. Senior 2 developers should be proficient in
    shell scripting and other scripting languages.
-   Senior 2 developers are expected to have a strong understanding of software
    versioning and should be able to create a release branch with a version
    number and update the project's Info.plist file accordingly.
-   The task also requires Senior 2 developers to have experience with merging
    and pushing changes to remote repositories.

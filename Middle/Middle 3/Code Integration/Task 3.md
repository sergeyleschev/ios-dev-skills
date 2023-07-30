# Task 3

Task:

You have been working on a project with a team of developers, and you've been
assigned the task of resolving a merge conflict in Git. The conflict is in a
file called "ViewController.swift" and involves conflicting changes made to a
function called "updateUI()". Your task is to resolve the conflict and commit
the changes.

Solution:

To resolve the conflict, you should first open the file in Xcode and look for
the conflicting code sections. The conflicting sections will be marked with
"<<<<<<< HEAD", "=======", and ">>>>>>> [commit hash]".

You'll need to review the changes made in both sections and determine which
changes are correct. Once you've determined which changes to keep, you can
delete the conflict markers and save the file.

After resolving the conflict, you can stage the changes using the "git add"
command and commit the changes using the "git commit" command with an
appropriate commit message.

It's also a good practice to push the changes to the remote repository using the
"git push" command to ensure that everyone on the team has access to the latest
code changes.

In terms of differences between Middle 3 and Middle 2 level developers, a Middle
3 developer should have a deeper understanding of Git and be able to quickly and
confidently resolve merge conflicts. They should also have a better
understanding of how to push and pull changes to/from remote repositories and
understand how to use Git effectively for collaboration within a team.

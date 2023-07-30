# Task 3

Task:

You are working on a team project with multiple developers. The project is
stored in a git repository hosted on GitHub. Your team lead has assigned you to
review the code changes made by a teammate before merging them into the main
branch.

Write a command or series of commands that you can use to review the changes
made by your teammate in a specific file named "ViewController.swift".

Solution:

1. Start by fetching the latest changes from the remote repository using the
   following command:

```bash
git fetch
```

2. Switch to the branch that contains your teammate's changes:

```bash
git checkout teammate-branch
```

3. Review the changes made by your teammate in the "ViewController.swift" file:

```bash
git diff main -- ViewController.swift
```

4. If you need to see more context around the changes, you can add the **`U`**
   flag followed by the number of lines of context you want to include:

```bash
git diff main -- ViewController.swift -U3
```

5. Once you have reviewed the changes, you can switch back to the main branch:

```bash
git checkout main
```

These commands demonstrate a good understanding of git and show that the
developer can review code changes made by a teammate before merging them into
the main branch. Additionally, the use of the **`-U`** flag to add more context
to the diff output shows attention to detail and consideration for code quality.

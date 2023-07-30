# Task 4

Task: Implement a Git pre-commit hook that checks if any committed file contains
a TODO comment and reminds the developer to address it before committing.

Solution:

1. Create a pre-commit hook file in the **`.git/hooks`** directory with the
   following command:

    **`touch .git/hooks/pre-commit`**

2. Open the pre-commit hook file in a text editor and paste the following code:

    ```bash
    #!/bin/bash

    # Check for TODO comments in files being committed
    TODO_COUNT=$(git diff --cached --name-only | xargs grep -i todo | wc -l)
    if [ "$TODO_COUNT" -ne 0 ]; then
        echo "WARNING: You have $TODO_COUNT TODO comments in your code. Please address them before committing."
        exit 1
    fi
    ```

3. Save and close the file.
4. Make the pre-commit hook executable with the following command:

    **`chmod +x .git/hooks/pre-commit`**

Now, whenever a developer attempts to commit a file that contains a TODO
comment, they will see a warning message reminding them to address it before
committing. This helps ensure that all code committed to the repository is clean
and free of lingering TODOs.

Difference between Senior 1 and Senior 2: The Senior 2 developer is expected to
have a deeper understanding of Git and how to customize its behavior with hooks.
They are also expected to have a strong attention to detail and be proactive in
addressing potential issues before they arise. This task requires the Senior 2
developer to create a custom Git hook to enforce a specific coding standard,
demonstrating their ability to create automated processes to improve code
quality.

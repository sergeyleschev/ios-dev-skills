# Task 1

Task:

Your team has been tasked with integrating a new third-party library into your
project. The library is available as a git repository and should be included as
a git submodule in your project. Write the necessary git commands to add the
submodule and explain why this approach is preferable to simply copying the
library files into your project.

Solution:

To add the third-party library as a git submodule in your project, you can use
the following command:

```bash
git submodule add <URL of the library's git repository> <relative path to the submodule in your project>
```

For example, if the library's git repository URL is
**`https://github.com/example/library.git`** and you want to add it as a
submodule in a **`Libraries`** directory in your project, you can use the
following command:

```bash
git submodule add https://github.com/example/library.git Libraries/library
```

This approach is preferable to simply copying the library files into your
project because:

1. It allows you to easily update the library to a new version or switch to a
   different library implementation without having to manually track and update
   the library files in your project.
2. It keeps the library code separate from your project code, making it easier
   to manage dependencies and reducing the risk of conflicts or unintended
   changes to the library files.
3. It also allows other developers on your team to easily access and update the
   library code without having to manually add or update the files in their own
   copies of the project.

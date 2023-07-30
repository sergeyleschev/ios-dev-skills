# Task 5

Task:

You are working on a project that requires automated testing to be set up as
part of the CI process. Your task is to create a script that can run the tests
automatically and report any failures.

Solution:

You can use Xcode's built-in test framework, XCTest, to run automated tests. You
can create a script that uses xcodebuild to build and run the tests, then parse
the output to check for any failures. Here is an example script:

```bash
#!/bin/bash

# Build and run tests
xcodebuild test -workspace MyProject.xcworkspace -scheme MyScheme -destination 'platform=iOS Simulator,name=iPhone 12' | xcpretty

# Check for test failures
if [ ${PIPESTATUS[0]} -ne 0 ]; then
    echo "Tests failed!"
    exit 1
else
    echo "Tests passed!"
    exit 0
fi
```

This script uses xcodebuild to build and run tests, and pipes the output to
xcpretty to make it more readable. It then checks the exit code of xcodebuild to
see if any tests failed, and exits with an error code if there were any
failures.

To integrate this script into your CI process, you can add it as a build step in
your CI tool (e.g. Jenkins, Travis CI, CircleCI).

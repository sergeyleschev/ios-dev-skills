# iOS Dev Skills. Performance Review.

### Department Structure:

-   Trainee
-   [Junior 1](Junior/Junior%201)
-   [Junior 2](Junior/Junior%202)
-   [Junior 3](Junior/Junior%203)
-   [Middle 1](Middle/Middle%201)
-   [Middle 2](Middle/Middle%202)
-   [Middle 3](Middle/Middle%203)
-   [Senior 1](Senior/Senior%201)
-   [Senior 2](Senior/Senior%202)

### Performance Review Schedule:

-   Trainee: Performance review every 3 months.
-   Junior 1, Junior 2, Junior 3: Performance review every 3 months.
-   Middle 1, Middle 2, Middle 3: Performance review every 6 months.
-   Senior 1, Senior 2: Performance review every 6 months.

Note: The performance review schedule may vary depending on the specific
company's policies and guidelines.

### List of topics that a developer needs to know in order to pass a performance review.

|                        | [Junior](Junior)                                        | [Middle](Middle)                                                | [Senior](Senior)                                                        |
| ---------------------- | ------------------------------------------------------- | --------------------------------------------------------------- | ----------------------------------------------------------------------- |
| Ability                | can make a news app talking to a JSON API               | can timely design and deliver fast and reliable chat module     | can establish team behaviour standards with non-fanatical ideas         |
| Code Integration       | uses git to move code around                            | has an opinion about GitFlow                                    | has ideas how to build a CI process and automate chores                 |
| Paradigms              | got the idea of OOP                                     | got hands dirty with FRP                                        | brings value from other platforms and paradigms                         |
| Dependencies           | knows how to use Cocoapods                              | knows why apps can't use SPM, but Carthage is an option         | knows why it is essential to own/reduce dependencies                    |
| Platform               | uses Array, Dictionary and Set                          | knows Value/Reference types and Equatable/Hashable              | knows the details of method dispatch of both Swift and Obj-C            |
| Client-Server Protocol | getting that JSON from the Internet is a piece of cake! | making a WebSocket-based real-time chat is feasible             | building a video chat is an achievable challenge                        |
| Reference              | uses StackOverflow as a single source of truth          | often uses official documentation                               | asks platform developers and can reverse engineer                       |
| Memory                 | knows how to avoid and fix a memory leak                | knows NSPointerArray and why structs increase binary size       | has a strategy to reduce out-of-memory crashes                          |
| UI                     | can build basic UI in the Interface Builder             | has reasons to make UI in code                                  | can take layout and diff calculation to non-main thread                 |
| Multithreading         | asyncAfter is a friend, @synchronize all the things     | asyncAfter is an enemy, and thread synchronization is a problem | understands multithreading problems beyond the deadlock                 |
| Attitude               | expects others to teach and guide during development    | discusses design with the team to share decision                | takes responsibility for design decision made by teammates              |
| Design Patterns        | understands Delegation, Target-Action and MVC idea      | is proficient at Observer, Facade and Mediator patterns         | knows the sweet spot between dependency injection and service locator   |
| Product Quality        | the app is tested if it works on my phone               | writes unit tests and tried TDD and UI tests                    | defines a maintainable test pyramid with non-overlapping coverage areas |

[Junior](Junior)

[Middle](Middle)

[Senior](Senior)

The average time to complete a task or answer a question is 10 to 15 minutes.

The average time to complete a performance review is 2-3 hours.

There are 13 sections in total. One task is provided for the solution (out of 5
in the section) at the choice of the interviewer. It is possible to provide a
second chance (the second task out of 5) if the first one causes difficulty,
with a score adjustment by a factor of ~ 0.5.

### For Contributors

Fork the original project https://github.com/sergeyleschev/ios-dev-skills by
clicking the Fork button. Clone the fork to your computer:

```bash
git clone https://github.com/my_account/ios-dev-skills
cd ios-dev-skills
```

Create a new branch:

```bash
git checkout -b myfix
Set up the upstream to the original project:
```

```bash
git remote add upstream https://github.com/sergeyleschev/ios-dev-skills
```

Make the necessary changes to the files.

Commit and push the fixes:

```bash
git add .
git commit -am "My fixes"
git push -u origin new_branch
```

Go to your project at https://github.com/my_account/ios-dev-skills and click the
"Compare & pull request" button. Describe the problem that the Pull Request
solves, providing a brief explanation of why this change was made. You're
awesome! ;)

P.S. for formatting, you can use

```bash
prettier --write "**/*"
```

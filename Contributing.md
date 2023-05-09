# How to contribute
First, thanks for taking the time to contribute to our project! There are many ways you can help out.

### Questions

If you have a question that needs an answer, [create an issue](https://help.github.com/articles/creating-an-issue/), and label it as a question.

### Issues for bugs or feature requests

If you encounter any bugs in the code, or want to request a new feature or enhancement, please [create an issue](https://help.github.com/articles/creating-an-issue/) to report it. Include a label to indicate what type of issue it is.

### Contribute Code
We welcome your pull requests for bug fixes. To implement something new, please create an issue first so we can discuss it together.

***Creating a Pull Request***
Please follow [best practices](https://github.com/trein/dev-best-practices/wiki/Git-Commit-Best-Practices) for creating git commits.

When your code is ready to be submitted, [submit a pull request](https://help.github.com/articles/creating-a-pull-request/) to begin the code review process.

***Testing***
To run all test files in the root folder
```shell
go test -v ./...
```
Tests should all pass before and after any work that you do. If they
do not; please reach out to the maintainers for help.

Separately, all test files are also run when a pull request is created.

## Code of Conduct

We encourage inclusive and professional interactions on our project. We welcome everyone to open an issue, improve the documentation, report bug or submit a pull request. By participating in this project, you agree to abide by the [Code of Conduct](Code-of-Conduct.md). If you feel there is a conduct issue related to this project, please raise it per the Code of Conduct process and we will address it.

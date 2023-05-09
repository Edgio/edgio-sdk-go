# Onboarding

## Purpose
This document is a collection of all onboarding-related information, tips & 
tricks, etc. for first-time SDK contributors.

## Learning Resources
The internet contains a plethora of learning resources for the Go language. 
Below are sources that we find useful:
- [Go Get Started Guide](https://go.dev/learn/)
    - Also lists additional learning resources.
- [Pluralsight (License Required)](https://www.pluralsight.com/)
    - We recommend the [Getting Started With Go](https://app.pluralsight.com/library/courses/getting-started-with-go/) course for an excellent guide to setting up your 
    local development environment.
- [Go by Example](https://gobyexample.com/)
    - Ideal for those who learn best by doing.
- [The Go Playground](https://go.dev/play/)
    - Sandbox for playing with Go code.
- [Go Docs](https://golang.org/doc/)
    - Landing page for many Go resources e.g. learning, concepts, etc.
- [Effective Go](https://go.dev/doc/effective_go)
    - Outlines community-accepted code style and best practices.
- [Our Go Guide](https://github.com/EdgeCast/ec-sdk-go/blob/main/Go.md)
    - Best practices and code style our team adheres to.

## Local Environment Setup

Below is a breakdown of the setup:
1. Install Go - [download](https://go.dev/dl/)
2. Install Git - [download](https://git-scm.com/downloads)
3. Install Visual Studio Code - [download](https://code.visualstudio.com/download)
4. Set up Git access for your machine
    - Use a Git client like [Sourcetree](https://www.sourcetreeapp.com/) or
    [GitHub Desktop](https://desktop.github.com/)
    - [Create an SSH Key](https://docs.github.com/en/authentication/connecting-to-github-with-ssh) 
    for your GitHub account and add it to your local machine.
5. Install the Go Extension for VS Code
    - In VS Code, open the Extensions menu and search for "Go". The developer 
    should be "Go Team at Google".
6. Install any suggested Go tools as prompted by Visual Studio
7. Clone the [ec-sdk-go](https://github.com/EdgeCast/ec-sdk-go) repository.
8. Set `golangci-lint` as your linter:
    - Navigate to VS Code's settings.
    - Search for `go.lintTool`.
    - In the Go: Lint Tool dropdown, select `golangci-lint`.
9. Set up VS Code to run `gofumpt` automatically when saving a `.go` file:

Install
```bash
go install mvdan.cc/gofumpt@latest
```

Open VS Code's settings and search for `gopls`.
Click the link to edit settings.json directly and add the following:

```json
  "go.useLanguageServer": true,
  "gopls": {
    "formatting.gofumpt": true,
  },
```

## Development Workflow
Create a branch off of main and begin coding! 

### Testing
#### Unit Testing
Ensure that all unit tests pass before submitting a pull request. 

1. Open a terminal at the root of the repository.
2. Run `go test ./…` from the repository root. 

#### Regression Testing
Consider the scope of changes in your PR and whether it is necessary to run some 
or all of the example files located in the [example](example) folder as 
end-to-end tests to identify regressions.

### Release
Create a new release in GitHub with the appropriate vM.m.r semantic version e.g. 
v0.1.8 via the releases tab. Ensure to create a tag on the release screen using 
the same name. This process will be replaced with a GitHub action in the future.

In your release, be sure to include each section below. If there are no changes
for a section, omit it. Refer to existing 
[releases](https://github.com/Edgio/edgio-sdk-go/releases).
- Breaking Changes
    - Alert consumers of the SDK of any changes that can break their code.
- New Features
- Bug Fixes and Enhancements
    - Enhancements can include performance improvements, code optimization, etc.
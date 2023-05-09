# Go Development and Style Guide
Jump to:
* [Development Environment](#development-environment)
* [Code Style](#code-style)
* [Useful Links](#useful-links)

## Development Environment
We recommend Visual Studio Code - it's what we use for this SDK. 
You can download it [here](https://code.visualstudio.com/download).

### Go Extension
Install the Go extension for VS Code. 

Set it up to use `golangci-lint`: 
- Navigate to VS Code's settings.
- Search for `go.lintTool`.
- In the Go: Lint Tool dropdown, select `golangci-lint`.

If you are interested in the linters it provides, refer to the [golangci-lint docs](https://golangci-lint.run/).
It will load the YAML configuration at the root of the project named `.golangci.yml`.

## Code Style
In general, we follow the code styles that can be found in the [Useful Links](#useful-links) below.

### Naming
#### Packages
By convention, packages are given lower case, single-word names; there should be no need for underscores or mixedCaps. Another convention is that the package name is the base name of its source directory. The importer of a package will use the name to refer to its contents, so exported names in the package can use that fact to avoid repetition. For example, bufio.reader not bufReader.

#### File Names
Keep it short, but still meaningful; Use lower case and use snake_case instead of mixedCaps. 

#### Variables
A variable's name should be short but meaningful. 
Examples: 
- Use `svc` instead of service or myService.  Use `r` or `repo` instead of repository or myRepository.
- Use `ctx` for context.Context, `newCtx` for new context.
- In loops: Prefer i, j, k fo indexes.
- In maps: use k and v for key and value.
- Use camelCasing; `newCtx` not `new_ctx`. 

Constants:
- Use mixedCaps for naming constants.
- Do not use underscores or all caps unless it's generated code. So, use `statusActive` instead of `STATUS_ACTIVE`.
- Group constants together with a prefix. e.g. status constants would look like `statusActive`, `statusPending`, etc.

Errors:
- Error variable names should start with Err. Use `ErrNotFound` instead of `NotFoundError`. Note that it's Err, not Error.
- When defining an error type, "Error" should be the suffix of the type name. Use `NotFoundError` instead of `ErrNotFound`.
- Error strings should be all lower case (this is enforced by the linter) e.g. `resource not found`.

#### Functions
- Use mixedCaps for naming functions. 
- If a function receives a context, the context must be the first parameter and its name should be ctx. 
- Function name should start with a verb. example, `deleteSomething` instead of `somethingDelete`.
- Getters SHOULD NOT use a `Get` prefix e.g. `person.Name()`
- Setters SHOULD use a `Set` postfix e.g. `person.SetName()`

#### Interfaces
By convention, one-method interfaces are named by the method name plus an -er suffix or similar modification to construct an agent noun: Reader, Writer, Formatter, CloseNotifier etc.

### JSON Marshaling with Go
Use struct tags to control how structs are marshaled and unmarshaled:
```
type User struct {
    FirstName string `json:"first_name"` // key will be "first_name"
    BirthYear int `json:"birth_year"` // key will be "birth_year"
    Email string `json:"email, omitempty"`
}
```

*Always use json struct tags in model objects!*
- Use "omitempty" tag for fields that should be omitted from the encoding if the field has an empty value, defined as false, 0, a nil pointer, a nil interface value, and any empty array, slice, map, or string.
- Be careful with omitempty - some APIs treat the absence of a property differently from it being null or a default value.
- Use "-" tag for fields that need to be ignored.

## Useful Links
* [A tour of Go](https://tour.golang.org)
* [Golang wiki](https://github.com/golang/go/wiki)
* [Effective Go](https://golang.org/doc/effective_go.html)
* [Go by Example](https://gobyexample.com)
* [JSON and GO](https://go.dev/blog/json)
* [Common Style Issues in Go](https://github.com/golang/go/wiki/CodeReviewComments)
* [Edgecast Go Style](https://gitlab.edgecastcdn.net/edgecast/docs/developer-guide/-/blob/master/style/go/go.md)
  * Please note that this link is only accessible by Edgio employees. 

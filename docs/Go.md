## Learning Go

* Book: [The Go Programming Language](https://www.gopl.io) by Alan A. A. Donovan and Brian W. Kernighan
* eBooks: [For the Love of Go](https://bitfieldconsulting.com/books) by John Arundel
* Video Course: [Go: The Complete Developer's Guide](https://www.udemy.com/course/go-the-complete-developers-guide/) by Stephen Grider

## Misc Resources

* 🗒️ [Using `ldflags` to set version information for CLI apps](https://www.digitalocean.com/community/tutorials/using-ldflags-to-set-version-information-for-go-applications)
* 📺 [33m talk](https://www.youtube.com/watch?v=MHv6cWjvQjM) by Liz Rice where she live codes the process of creating a basic container with Go
* 🗒️ [The Tao of Go](https://bitfieldconsulting.com/golang/tao-of-go)

## Go Modules

### Use a local copy of a module

This is useful for local development when working on two modules in parallel (e.g. a client library and an app that uses it).

```
# Run go mod edit first, even if the module is not in go.mod yet
go mod edit -replace=github.com/USERNAME/REPO=/PATH/TO/LOCAL/REPO
# Get the module using its normal url
go get github.com/USERNAME/REPO
```

### Use a forked version of a module

This is useful when you want to use a fork of a module (e.g. a branch where the PR has not been merged upstream yet):

```
# @BRANCH_NAME is optional
go mod edit -replace=github.com/UPSTREAM_USERNAME/REPO=github.com/FORK_USERNAME/REPO@BRANCH_NAME
go get github.com/UPSTREAM_USERNAME/REPO
```

Use `github.com/UPSTREAM_USERNAME/REPO` in the `import` statements also (not the URL of the fork).

## Learning Go

### Resources I've read/watched and would recommend

* :book: [The Go Programming Language](https://www.gopl.io) by Alan A. A. Donovan and Brian W. Kernighan
* :book: (series) [For the Love of Go](https://bitfieldconsulting.com/books) by John Arundel
* 📺 (course) [Go: The Complete Developer's Guide](https://www.udemy.com/course/go-the-complete-developers-guide/) by Stephen Grider
* 📖 [Distributed Services with Go](https://pragprog.com/titles/tjgo/distributed-services-with-go/) by Travis Jeffery - Walks through building a distributed system like Kafka.
* 📺 [GopherCon 2019: Marwan Sulaiman - Handling Go Errors](https://www.youtube.com/watch?app=desktop&v=4WIhhzTTd0Y)

### Resources I'm interested in checking out

* [Powerful Command-Line Applications in Go](https://pragprog.com/titles/rggo/powerful-command-line-applications-in-go/)
* [Blackhat Go](https://nostarch.com/blackhatgo) has interesting chapters on tcp and http. Could be a fun way to learn about those and go. 
* [Networking with Go](https://nostarch.com/networkprogrammingwithgo)
* [Go Programming Blueprints](https://www.amazon.com/Programming-Blueprints-real-world-production-ready-cutting-edge-ebook/dp/B01GQCQ8OW) by Mat Ryer, each chapter has a real world example, several are about web development 


### Misc Resources

* 🗒️ [Using `ldflags` to set version information for CLI apps](https://www.digitalocean.com/community/tutorials/using-ldflags-to-set-version-information-for-go-applications)
* 📺 [33m talk](https://www.youtube.com/watch?v=MHv6cWjvQjM) by Liz Rice where she live codes the process of creating a basic container with Go
* 🗒️ [The Tao of Go](https://bitfieldconsulting.com/golang/tao-of-go)
* [Go Recipes blog](https://go-recipes.dev/)
* 📺 [Ardan Labs (Bill Kennedy) YouTube Channel](https://youtube.com/channel/UCCgGRKeRM1b0LTDqqb4NqjA)


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

# gopherjs-fail-example


## example

```console
gopherjs-fail-example/main$ GOPHERJS_GOROOT="$(go1.18.10 env GOROOT)" gopherjs build
failed to expand patterns []: failed to list packages in the primary context: failed to list packages on FS: go tool error: /home/makki/Development/go/bin/go list -e -compiler=gc -tags=netgo,purego,math_big_pure_go,gopherjs -installsuffix= -f={{.ImportPath}} --: exit status 1
go: updates to go.mod needed; to update it:
        go mod tidy
```

The GopherJS build failed under the condition:
- Go 1.21.0 installed under the `$PATH`
- `gopherjs build` module targets a version earlier than 1.21.0
  - In this example, `main` module targets `go 1.18`
- Imported package targets `go 1.21.0`
  - Imported `submod` package targets `go 1.21.0`
  - It can be compiled with Go 1.18.10

## version info
```console
$ go version
go version go1.21.0 linux/amd64
$ go1.18.10 version
go version go1.18.10 linux/amd64
$ gopherjs version
GopherJS 1.18.0-beta3+go1.18.10
```

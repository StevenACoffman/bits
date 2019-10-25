# bits

### Quick Start

```console
$ go mod init <module name>
$ git init .
$ git add go.mod
$ git commit -avm "new go module"
$ export bt=$(mktemp); curl -s -L https://raw.githubusercontent.com/freeformz/bits/v0.0.6/mage/setup.sh > $bt && (bash $bt; rm -f $bt); unset bt
...
```

Creates a defaults magefile.go, .circleci config, .gitignore, & .golangci.yml

```console
$ mage -f
Targets:
  go:checkVersion        checks that the version of go being used is the version specified or the latest version
  go:cover               runs go tool cover with default args set from `CoverArgs`
  go:coverage            opens the coverage output in your browser (runs "go tool cover -html=coverage.out")
  go:test                runs `go test` with default args set from `TestArgs`
  golangcilint:remove    removes all cached versions of golangci-lint
  golangcilint:run       runs golangci-lint using RunArgs
```

### Targets

#### Go Namespace

`go:checkVersion` - Asserts that the version is use is the version specified. If the version specified ends in `.x` or only has two parts (`go1.13`) it is expanded to the most recent patch version of that go release. Modify the version by specifying `gons.Version` in your magefile.

`go:cover` - Generate cover file. Modify the arguments by specifying `gons.CoverArgs` in your magefile.

`go:coverage` - Generates coverage information and opens it in your browser. Modify the arguments by specifying `gons.CoverArgs` in your magefile.

`go:test` - Runs go test. Modify the arguments by specifying `gons.TestArgs` in your magefile.

#### Tool Namespace

`golangclilint:remove` - Removes all cached versions of golangci-lint.

`golangcilint:run` - Runs golangci-lint. Modify the arguments by specifying `toolns.GolangciLint.RunArgs` and change the version by specifying `toolns.GolangciLint.Version` in your magefile.
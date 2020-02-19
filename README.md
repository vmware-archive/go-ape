[![GoDoc](https://godoc.org/github.com/pivotal/image-relocation?status.svg)](https://godoc.org/github.com/pivotal/go-ape)
[![Go Report Card](https://goreportcard.com/badge/pivotal/image-relocation)](https://goreportcard.com/report/pivotal/go-ape)
[![Build Status](https://dev.azure.com/projectriff/go-ape/_apis/build/status/pivotal.go-ape?branchName=master)](https://dev.azure.com/projectriff/go-ape/_build/latest?definitionId=6&branchName=master)
[![codecov](https://codecov.io/gh/pivotal/go-ape/branch/master/graph/badge.svg)](https://codecov.io/gh/pivotal/go-ape)

# go-ape

go-ape provides some file utilities in two packages:
* `pkg/filecopy` for copying files (hence the "ape" in "go-ape")
* `pkg/furl` for reading local files and remote urls in a consistent way

It was initially developed on macOS and then made to work on Windows.

# Installing

Install is easy, all you need to do is
```
go get github.com/pivotal/go-ape
```

# Usage
Once installed, import go-ape in your application 
```
import "github.com/pivotal/go-ape"
```
## Read files
Then start reading files like so:
```
content, err := furl.Read(filePath, "")
```
Here filePath can be a path on the local file system (unix OR windows) or a URL.


## Copy
You can also copy files or directories using:
```
filecopy.Copy(outputPath, inputPath)
```

Please see the [godoc](https://godoc.org/github.com/pivotal/go-ape) for more information.

# Alternatives

https://github.com/otiai10/copy copies files and directories, but incompatibly to go-ape (replacing the implementation here with otiai10/copy caused numerous test failures).
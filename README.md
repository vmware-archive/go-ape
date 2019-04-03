[![GoDoc](https://godoc.org/github.com/pivotal/image-relocation?status.svg)](https://godoc.org/github.com/pivotal/go-ape)
[![Go Report Card](https://goreportcard.com/badge/pivotal/image-relocation)](https://goreportcard.com/report/pivotal/go-ape)
[![Build Status](https://dev.azure.com/projectriff/go-ape/_apis/build/status/pivotal.go-ape?branchName=master)](https://dev.azure.com/projectriff/go-ape/_build/latest?definitionId=6&branchName=master)
[![codecov](https://codecov.io/gh/pivotal/go-ape/branch/master/graph/badge.svg)](https://codecov.io/gh/pivotal/go-ape)

# go-ape

go-ape provides some file utilities:
* Copy files (hence the "ape" in "go-ape")
* Read local and remote files in a consistent way

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
content, err := fileutils.Read(filePath, "")
```
Here filePath can be a path on the local file system (unix OR windows) or a URL.

Read contract:
```
// Read reads the contents of the specified file. If the file is a relative path, it is relative to base.
// Either file or base may be URLs.
func Read(file string, base string) ([]byte, error)
```

## Copy
You can also copy files/folders using:
```
checker := fileutils.NewChecker()
copier := fileutils.NewCopier(os.Stdout, checker)
copier.Copy(outputDir, inputDir)
```
Copy contract:

		Copy copies a source file to a destination file. File contents are copied. File mode and permissions
		(as described in http://golang.org/pkg/os/#FileMode) are copied.

		Directories are copied, along with their contents.

		Copying a file or directory to itself succeeds but does not modify the filesystem.

		Symbolic links are not followed and are copied provided they refer to a file or directory being copied
		(otherwise a non-nil error is returned). The only exception is copying a symbolic link to itself, which
		always succeeds.

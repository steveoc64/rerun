# Rerun II

## Forked from skelterjon/rerun

### Whats Different ?

When coding in and IDE, you sometimes want to build from the IDE to collect errs and what not.

However, rerun will also trigger a build - usually slightly behind the manual build .. so often it 
will run into the "cant write xxx - text file busy" error, which kills the rerunner.

This change treats a text file busy error as exactly this case, waits a second, and tries again. Easy.

### Original Documetation

Use like ```rerun github.com/skelterjohn/go.uik/uiktest```

Usage: ```rerun [--test] [--build] [--race] [--no-run] <import path> [arg]*```

For any go executable in a normal GOPATH workspace, rerun will watch its source,
rebuild, retest, and rerun. As long as ```go install <import path>``` works,
rerun will be able to find it.

Along with the target's source, rerun also watches the source of all
the target's non-GOROOT dependencies.

When using flag `--test`, rerun executes `go test`. If tests fail, rerun will not continue to build and/or run the program.

Flag `--build` makes rerun execute `go build` in the local folder, creating an executable.

Flag `--no-run` omits actually running the program. This is useful if you only wish to test and/or build.

Flag `--race` will test/build/run the program with race detection enabled.

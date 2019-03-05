# Installation

To use NetAuth you will obviously need to install it.  You may either
install from source or from a packaged binary.  The NetAuth project
does not provide binaries for download.

## From Packages

If your distribution provides a package for NetAuth that is likely the
easiest way to install it.  Make sure that your distribution packages
a recent version if you choose to go this route.

At present, the following distributions are known to package NetAuth:

  * Void Linux

## From Source

If your distribution does not provide packages for NetAuth, you will
need to install from source.  To install from source you will need a
working Go environment at or above version 1.10.  Your environment
must also have the `dep` dependency manager available, either via
native package or via installation with `go get`.

### Obtain the Source

Obtain the source with `go get` as shown.  Dependencies are not
vendored, so this will not attempt to build the source.

```shell
$ go get -d github.com/NetAuth/NetAuth/cmd/...
```

This will download the source to your GOPATH.  Now you should obtain
the dependencies:

```shell
$ cd $GOPATH/src/github.com/NetAuth/NetAuth
$ dep ensure
```

### Building the Binaries

Once you have obtained the source, you may build the server and
client.

```shell
$ go get github.com/NetAuth/NetAuth/cmd/...
```

Your compiled binaries will be in `$GOPATH/bin/`.  As with all Go
programs, the binary artifacts are statically compiled and may be
copied anywhere on your filesystem.

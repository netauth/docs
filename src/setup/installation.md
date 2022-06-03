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

If your distribution does not provide packages, or if you do not wish
to use them, you can compile from source:

```shell
$ git clone -b <version> git://github.com/netauth/netauth
$ cd netauth
$ go build -o netauthd github.com/netauth/netauth/cmd/netauthd
$ go build -o netauth github.com/netauth/netauth/cmd/netauth
$ go build -o nsutil github.com/netauth/netauth/cmd/nsutil
```

You can now copy the binaries to wherever your system stores binaries
that are locally managed.  Typically this will be `/usr/local/bin`.

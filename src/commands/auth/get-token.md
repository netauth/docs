# get-token

Obtain a token which can be used to authenticate future requests.

Because NetAuth uses cryptosystems that are by design slow in order to
ensure security, tokens are used to provide quick authentication after
initial verification is complete.

## Help Text

```
get-token
  Attempt to obtain a token from the specified server.
```

## Usage

The usage of `get-token` is equivalent to the usage of `auth`.  The
only exception is that the token is cached locally, and if the local
token is still valid then it will be returned without contacting the
server.

It is not necessary to manually call `get-token`.  All commands which
require tokens will invoke the token request if needed.  Tokens are
also good for some amount of time, so one token request can authorize
many commands.

## Example

```shell
$ netauth get-token
Secret:
Token obtained
```

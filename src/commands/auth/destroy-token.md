# destroy-token

Tokens will expire after a fixed amount of time, but in the event an
operator wishes to destroy a token immediately, `destroy-token` fills
this need.

## Help Text

```
destroy-token
  Attempt to destroy the local authority token.  This command will
  make a best effort attempt to remove the local token.
```

## Usage

The command will attempt to remove the token from local storage.  This
is a best effort attempt and is subject to the capabilities of the
local storage system.  In the event the token could not be removed an
error will be printed.

## Example

```shell
$ netauth destroy-token
Token destroyed
```

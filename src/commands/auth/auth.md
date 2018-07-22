# auth

Authenticate an entity.

## Help Text

```
auth
  Attempt to authenticate to the server specified.
```

## Usage

The auth command takes no flags, it will attempt to authenticate with
a NetAuth server.  In the case of successful authentication the exit
code will be 0, for all failure modes it will be non-zero.

The auth command can be useful for systems that can use external
authentication methods to shim in NetAuth support to systems that
would not otherwise have it.

## Example

```shell
$ netauth --entity foo --secret bar auth
Entity authentication succeeded

$ netauth --entity foo auth
Secret:
Entity authentication succeeded

$ netauth auth
Secret:
Entity authentication succeeded
```

# inspect-token

Inspect a token locally.

This command will attempt to inspect a token locally without
contacting the NetAuth server.  If successful, it will dump the
contents of the token to stdout.

## Help Text

```
inspect-token
  Inspect the token locally, printing its contents if it is valid.
```

## Usage

The inspect-token command will check a token locally to verify its
integrity and fitfulness for use.  The contents of the token are
printed but should not be assumed to be stable.  The contents of the
token are printed for debugging use only and may contain secure
information.

## Example

```
$ netauth get-token
Secret:
$ netauth inspect-token
{user [] 5}
```

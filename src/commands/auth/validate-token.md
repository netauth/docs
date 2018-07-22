# validate-token

While `inspect-token` only checks the token locally, `validate-token`
sends the token to a NetAuth server to request server-side validation.
This can be useful if the selected token implementation doesn't
support public key cryptography, and as such cannot provide client
side validation.

## Help Text

```
validate-token
  Send the token to the NetAuth server for validation.
```

## Usage

When called, `validate-token` will send the token to the server for
validation.  If the token is valid the exit code will be 0, for
invalid tokens the exit code will be non-zero.

## Example

```
$ netauth validate-token
Token verified
```

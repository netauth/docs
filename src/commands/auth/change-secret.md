# change-secret

Change the authentication secret for an entity.

## Help Text

```
change-secret --entity <ID>  --secret <secret>
Change the secret for the listed entity.  If no entity is provided the
entity specified by the top level flag will be used instead.  -entity string
        ID to change secret (default "maldridge")
  -secret string
        New secret (omit for prompt)
```

## Flags

  * `--entity`: Change the secret of this entity specifically.
  * `--secret`: Specify the secret on the command line.  Generally not
    recommended.

## Usage

The `change-secret` command does what the name implies.  If used like
the `passwd` command to change the secret of the calling entity, both
the original secret and the new secret must be provided.  A token will
not be sufficient to change the secret of the calling entity.

When changing the secret of another entity (as specified by the `--ID`
flag) then the calling entity must posses a token with the
`CHANGE_ENTITY_SECRET` capability.  This capability is allows an
entity holding it to change secrets arbitrarily for other entities.
This would generally be assigned to either a help-desk group or to a
system that can be used for a user to do self-service resets.

## Example

```shell
$ netauth change-secret
Secret:
New Secret:
Secret Changed
```

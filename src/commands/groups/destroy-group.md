# destroy-group

Remove an existing group from the server.

## Help Text

```
destroy-group --group <name>
Delete the named group.
  -group string
        Name of the group to destroy.
```

## Usage

Remove a group from the server by the given name.  The calling entity
must possess the `DESTROY_GROUP` capability.

## Example

```shell
$ netauth delete-group --group demo-group
Group removed successfully
```

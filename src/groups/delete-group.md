# delete-group

Remove an existing group from the server.

## Help Text

```
new-group --name <name>
Delete the named group.
  -name string
        Name for the new group.
```

## Usage

Remove a group from the server by the given name.  The calling entity
must possess the `DESTROY_GROUP` capability.

## Example

```shell
$ netauth delete-group --name demo-group
Group removed successfully
```

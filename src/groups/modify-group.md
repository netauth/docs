# modify-group

Modify the mutable fields on an existing group.

## Help Text

```
modify-group --name <name> [fields-to-be-modified]
Modify a group by updating the named fields to the provided values.
  -display_name string
        Group displayName (default "NO_CHANGE")
  -managed_by string
        Group that manages this group (default "NO_CHANGE")
  -name string
        Name of the group to modify
```

## Usage

Modify the fields on an existing group.  The calling entity must
possess the `MODIFY_GROUP_META` capability.  While you can change the
display name after a group has been created, it is still better to
make sure the display name and name are connected via some kind of
transformation, rather than being completely different.

Changing managed_by may significantly alter permissions, so consider
carefully the delta caused by granting management authority to the
entities in the named group.

## Example

```shell
$ netauth modify-group --name demo-group --display_name "Temporary Demo Group"
Group modified successfully
```

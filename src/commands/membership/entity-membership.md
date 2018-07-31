# entity-membership

Modify the direct membership of a specific entity.

## Help Text

```
entity-membership --entity <ID> --group <name> --<add|remove>

Add or remove the named entity from the named group.  Both the entity
and the group must exist already.
  -add
        Add the specified membership
  -drop
        Drop the specified membership
  -entity string
        ID of the entity to add to the group (default "maldridge")
  -group string
        Name of the group to add to
```

## Usage

Add or remove an entity from a group with this command.  Both actions
require either membership in a group's `managed_by` group, or
possession of the `MODIFY_GROUP_MEMBERS` capability.

## Example

```shell
$ netauth entity-membership  --entity demo --group demo-group --add
Membership updated successfully
```

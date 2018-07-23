# entity-membership

Modify the direct membership of a specific entity.

## Help Text

```
entity-membership --ID <ID> --group <name> --action <add|remove>

Add or remove the named entity from the named group.  Both the entity
and the group must exist already.
  -ID string
        ID of the entity to add to the group
  -action string
        Action to perform, must be 'add' or 'remove'
  -group string
        Name of the group to add to
```

## Usage

Add or remove an entity from a group with this command.  Both actions
require either membership in a group's `managed_by` group, or
possession of the `MODIFY_GROUP_MEMBERS` capability.

## Example

```shell
$ netauth entity-membership --action add --ID demo --group demo-group
Membership updated successfully
```

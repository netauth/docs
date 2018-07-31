# new-group

Create a new group.

## Help Text

```
new-group --name <name> [--display_name <display name>] [--gid_number <number>] [--managed_by <name>]
Allocate a new group with the given name and optional display name.
If the gid_number is not specified then the next available number will
be used.  The name and number cannot be changed once set, only the
displayName.
  -display_name string
        Display Name for the new group.
  -gid_number int
        Group ID Number for the new group (automatic if unset) (default -1)
  -managed_by string
        Group that will manage the new group
  -name string
        Name for the new group.
```

## Usage

Groups can be created by a user posessing the `CREATE_GROUP`
capability.  A group's name and number are immutable.  The number for
a group can be automatically allocated via the magic value `-1`.  This
mechanism is an opaque implementation detail with no guaranteed
behavior beyond allocating a number that is not presently in use.

The Display Name of a group may be changed at any time, but for sanity
should usually be some recognizable transformation of the name.

A group may delegate management of itself to a named group.  In this
case members of the named group may alter the group's metadata, add
and remove members, and perform other maintenance on the group.  It is
also possible to make a self managed group by making the `managed_by`
attribute equal the group's name.  Creating self managed groups is
supported (i.e. the group in the `managed_by` field need not exist at
creation).

## Example

```shell
$ netauth new-group --name demo-group --display_name "Demo Group"
New group created successfully
```

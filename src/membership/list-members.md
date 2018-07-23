# list-members

List members lists the members that are in a particular group.  There
is a special meta-group named `ALL` that has all entities on the
server as members.  Entities cannot be added to or excluded from `ALL`
since it isn't a "real" group.

## Help Text

```
list-members --group <group> [--fields field1,field2...]

List the members of the group identified by <group>.  Additionally
show only the named fields in the result.
  -fields string
        Fields to display
  -group string
        Name of the group to list
```

## Usage

Listing members works similarly to listing groups.

## Example

```shell
$ netauth list-members --group demo-group
ID: demo
Number: 7
GECOS: Demonstration Entity
```

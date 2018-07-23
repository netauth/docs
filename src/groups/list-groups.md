# list-groups

List all groups known to the server, or list all groups where a
specific entity is a member.

## Help Text

```
list-groups --entity <ID> --indirects [--fields field1,field2,field3...]

This command will return a list of groups, additional formatting
options can be selected for additional information.  If an entity is
specified, then only groups on that entity will be returned.
  -entity string
        Entity to obtain groups for, blank for all groups
  -fields string
        Comma seperated list of fields to display
  -indirects
        Include indirect group memberships (default true)
```

## Usage

When no entity is specified, list-groups returns a listing of all
known groups on the server.

When an entity is specified, the server will calculate the groups for
which the named entity is a member.  If the indirects option is
specified, then groups in which the entity has indirect membership are
included (this is generally what you want).

All entities are always a member of the special group `ALL`.  This
group will never be returned in the output of the `list-groups`
command.

## Example

```shell
$ netauth list-groups
Name: mygroup
Display Name: my awesome group
Number: 1

$ netauth list-groups --entity root
Name: mygroup
Display Name: my awesome group
Number: 1
```

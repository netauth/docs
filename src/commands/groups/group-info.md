# group-info

Summon all known information about a group.

## Help Text

```
group-info --name <name> [--fields field1,field2,field3...]

Return the fields of a group.  This will provide information on a
single group, as opposed to attempting to list all groups.
  -fields string
        Comma seperated list of fields to display
  -name string
        Name of the group to query
```

## Usage

Summon all information about a group and print it to stdout.  Fields
may be optionally filtered by providing a comma seperated list to the
`--fields` option.

## Example

```shell
$ netauth group-info --name demo-group
Name: demo-group
Display Name: Temporary Demo Group
Number: 9

$ netauth group-info --name demo-group --fields name,displayName
Name: demo-group
Display Name: Temporary Demo Group
```

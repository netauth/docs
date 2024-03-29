## netauth entity memberships

Memberships held by the specified entity

### Synopsis


The memberships command returns the memberships held by a particular
entity.  By default the output will include all attributes set on any
returned group.  To filter attributes use the --fields command to
specify a comma separated list of groups that you wish to return.


```
netauth entity memberships <entity> [flags]
```

### Examples

```
$ netauth entity memberships demo2
Name: demo-group
Display Name: Temporary Demo Group
Number: 9

$ netauth entity memberships demo2 --fields DisplayName
Display Name: Temporary Demo Group

```

### Options

```
      --fields string   Fields to be displayed
  -h, --help            help for memberships
```

### Options inherited from parent commands

```
      --config string   Use an alternate config file
      --entity string   Specify a non-default entity to make requests as
      --secret string   Specify the request secret on the command line
```

### SEE ALSO

* [netauth entity](netauth_entity.md)	 - Manage entities and associated data

###### Auto generated by spf13/cobra on 3-Jun-2022

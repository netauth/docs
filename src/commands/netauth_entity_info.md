## netauth entity info

Fetch information on an existing entity

### Synopsis


The info command can return information on any entity known to the
server.  The output may be filtered with the --fields option which
takes a comma seperated list of field names to display.  

```
netauth entity info <entity> [flags]
```

### Options

```
      --fields string   Fields to be displayed
  -h, --help            help for info
```

### Options inherited from parent commands

```
      --config string   Use an alternate config file
      --entity string   Specify a non-default entity to make requests as
      --secret string   Specify the request secret on the command line
```

### SEE ALSO

* [netauth entity](netauth_entity.md)	 - Manage entities and associated data

###### Auto generated by spf13/cobra on 25-Mar-2019
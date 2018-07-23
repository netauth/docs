# entity-info

Summon and display information on an entity, optionally filtering
fields.

## Help Text

```
entity-info --ID <ID>  [--fields field1,field2...]
Print information about an entity.  The listed fields can be used to
limit the information that is printed.
  -ID string
        ID for the new entity
  -fields string
        Comma seperated list of fields to display
```

## Usage

Summon and display all information known about an entity.  Information
retrieved may also be optionally filtered by providing a list of field
names.  If a particular field on an entity is empty, it will not be
displayed.  Some specialized fields are not displayed by this command
and instead must be queried by other commands.

## Example

```
$ netauth entity-info --ID demo
ID: demo
Number: 7
GECOS: Demonstration Entity

$ netauth entity-info --ID demo --fields ID,GECOS
ID: demo
GECOS: Demonstration Entity
```

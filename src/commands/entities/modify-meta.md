# modify-meta

Modify the metadata stored on an entity.  Note that some auxiliary
fields cannot be modified by this command and use other commands to
protect internal logic for those fields.

## Help Text

```
modify-meta --entity <ID> [fields-to-be-modified]
Modify an entity by updating the named fields to the provided values.
  -GECOS string
        Entity GECOS field (default "NO_CHANGE")
  -badgeNumber string
        Badge number for the entity (default "NO_CHANGE")
  -displayName string
        Display name associated with the entity (default "NO_CHANGE")
  -entity string
        ID for the entity to modify (default "maldridge")
  -graphicalShell string
        Graphical shell to be used by the entity (default "NO_CHANGE")
  -homedir string
        Home directory for the entity (default "NO_CHANGE")
  -legalName string
        Legal name associated with the entity (default "NO_CHANGE")
  -primary-group string
        Primary Group (default "NO_CHANGE")
  -shell string
        User command interpreter to be used by the entity (default "NO_CHANGE")
```

## Usage

The modify-meta command alters the flat fields associated with an
entity's meta-data.  The calling entity must either posses the
appropriate capability, `MODIFY_ENTITY_META`, or the change must be
requested by the entity itself.

Only fields specified will be changed, so there is no need to
re-specify a field who's value will remain the same.

## Example

```
$ netauth modify-meta --entity demo --GECOS "Demonstration Entity"
$ netauth entity-info --entity demo
ID: demo
Number: 7
GECOS: Demonstration Entity
```

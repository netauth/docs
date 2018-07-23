# modify-capabilities

Modify the capabilities assigned directly to an entity, or to a group.

## Help Text

```
modify-capabilities --capability <capability> <[--entity <ID>]|[--group <name>]> --mode <ADD|REMOVE>

Add or remove a capability from the named group or entity.  If both
are specififed (unsupported) then the group will be ignored.
  -capability string
        Capability to modify
  -entity string
        Entity to modify
  -group string
        Group to modify
  -mode string
        Mode, must be one of ADD or REMOVE (default "ADD")
```

## Usage

Capabilities can be added to entities directly or to a group.  The
preferred way to manage capabilities should be to a group, and then
add entities that require that capability to the group.

If an entity is provided to the command along with a group, the group
will be ignored.

## Example

```shell
$ netauth modify-capabilities --entity root --capability CREATE_ENTITY
Capability Modified

$ netauth modify-capabilities --entity root --capability CREATE_ENTITY
Capability Modified
```

# destroy-entity

Remove an existing entity from the server.  Note that entity
references are not cleaned up, so any downstream system must have
logic to determine when an entity has vanished from the server.  There
are no references on the server to clean, but systems that pull
incremental views may not notice the deletion.

## Help Text

```
destroy-entity --entity <ID>
Remove the specified entity from the server.  -entity string
        ID for the entity to be removed
```

## Usage

The destroy-entity command removes an entity from the server.  The
calling entity must posses appropriate capabilities to perform this
action, either via holding `GLOBAL_ROOT` powers or holding the
`DESTROY_ENTITY` capability.

No confirmation is requested and entity removal is not reversable.

## Example

```
$ netauth destroy-entity --entity demo
Entity removed successfully
```

# lock-entity

Locks and unlocks an entity.  Locked entities cannot successfully
authenticate, even when in possession of a valid secret.

## Help Text

```
lock-entity --<lock|unlock> --entity <entityID>

Lock or unlock an entity.  Each action requires a specific capability.
  -entity string
ID for the entity to modify (default "maldridge")
  -lock
Lock the named entity
  -unlock
Unlock the named entity
```

## Usage

The lock-entity command sets the locked bit in an entity's meta field.
Locking entities requires the `LOCK_ENTITY` capability.  Unlocking
entities requires the `UNLOCK_ENTITY` capability.  This permits
complex setups where an automated system might lock entities and
helpdesk staff can unlock them.

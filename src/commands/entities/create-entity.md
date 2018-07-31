# create-entity

Create a new entity.

## Help Text

```
create-entity --ID <ID> --number <number> --secret <secret>
  Create a new entity with the specified ID, number, and secret.
  number may be ommitted to select the next available number.
  Secret may be ommitted to leave unset.  -ID string
        ID for the new entity
  -number int
        number for the new entity (default -1)
  -secret string
        secret for the new entity
```

## Usage

Create a new entity on the NetAuth server.  The entity ID and number
must be unique and are both immutable.  If no number is provided, the
server will allocate a new number automatically.  The mechanism by
which this number is calculated is a reserved implementation detail.
The calling entity must possess appropriate capabilities to perform
this action, either via holding `GLOBAL_ROOT` powers or holding the
`CREATE_ENTITY` capability.

It is recommended to not supply the secret during creation since this
may leak the secret to the process table.  Instead non-machine
entities should go through a secret reset flow to set the initial
secret.  Machine entities should have a secret set from a secure
control point where the process table may be considered secure, or by
using the change-secret command to prompt for the new secret.

## Example

```shell
$ netauth create-entity --ID demo
New entity created successfully
$ netauth entity-info --ID demo
ID: demo
Number: 7
```

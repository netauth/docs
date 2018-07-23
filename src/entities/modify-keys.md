# modify-keys

Modify publicly visible keys that are stored on an entity.  Typical
uses include storing SSH public keys, GPG public keys, or public
certificates for easy retrieval by other entities.

## Help Text

```
modify-keys --ID <ID> --mode <ADD|LIST|DEL> --type <type> --key <key>

Modify the stored keys for an entity.  Key type must be specified as a
string of well known type.  This will be an uppercase version of the
key type like 'SSH' or 'GPG'.
  -ID string
        Entity to act on
  -key string
        Key contents
  -mode string
        Action to perform on keys (default "LIST")
  -type string
        Type of the key (default "SSH")
```

## Usage

The modify-keys command alters or lists the keys on a named entity.
The caller must be appropriately authorized to call this command,
either via capability (`MODIFY_ENTITY_KEYS`) or by being the entity
itself wishing to modify keys.

The default keytype is SSH, and keys must be quoted to avoid word
breaking by the shell.

When removing keys, lazy substring matching is used, therefore it is
only necessary to specify a unique string match for any part of the
key, usually the key comment.

## Example

```shell
$ netauth modify-keys \
    --ID demo \
    --mode ADD \
    --key "ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIIHqv36a+nr6xf2gZhdR2zvkxJnxKku892Z4LjkQjA7t demo@demoKey"

$ netauth modify-keys --ID demo --mode LIST
Type: SSH; Key: ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIIHqv36a+nr6xf2gZhdR2zvkxJnxKku892Z4LjkQjA7t demo@demoKey

$ netauth modify-keys --ID demo --mode DEL roaming
```

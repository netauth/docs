# untyped-meta

Manage untyped metadata on entities and groups.

## Help Text

```
untyped-meta --<entity|group> --<read|clearfuzzy|clearexact|upsert> --key <key> --value [value]

Manage untyped metadata associated with groups and entities.
Clearfuzzy strips ordering values from keys before clearing, whereas
clearexact removes a key with an exact match.  Upsert either inserts a
new value, or updates an existing one, and tries to do the right thing
either way.  Key and Value are always strings, key may not contain the
reserved rune ':'.
  -clear-exact
          Clear keys with exact matching
  -clear-fuzzy
          Clear keys with partial matching
  -entity string
          ID for the entity to modify
  -group string
          Name for the group to modify
  -key string
          Key to act on
  -read
          Read the value specified by 'key' including ordered results
  -upsert
          Insert/Update a value for a particular key
  -value string
          Value to act with
```

## Usage

The `untyped-meta` command can be used to add, remove, and retrieve
untyped metadata on an entity or group.  Only one entity or group may
be acted on at a time.  Specifying both `--entity` and `--group` will
result in an error.

Exactly one action may be performed at one time.  Actions include
`--read`, `--upsert`, `--clear-fuzzy`, and `--clear-exact`.  All
options require `--key` to be provided, and `--upsert` requires that
`--value` also be set.

A special key '*' is provided to summon all keys and values for an
entity or group.

## Example

```shell
$ netauth untyped-meta --entity root --read --key '*'
k1: v1
$ netauth untyped-meta --entity root --upsert --key k2{0} --value these
$ netauth untyped-meta --entity root --upsert --key k2{1} --value are
$ netauth untyped-meta --entity root --upsert --key k2{2} --value ordered
$ netauth untyped-meta --entity root --read --key k2
k2: these
k2: are
k2: ordered
$ netauth untyped-meta --entity root --clear-exact --key k2{1}
$ netauth untyped-meta --entity root --read --key k2
k2: these
k2: ordered
$ netauth untyped-meta --entity root --clear-fuzzy --key k2
$ netauth untyped-meta --entity root --read --key k2
# No Output
```

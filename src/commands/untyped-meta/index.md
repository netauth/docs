# Untyped Metadata

While NetAuth is not a directory, it is acknowledged that even a small
amount of directory-like services would greatly extend its
functionality.  This is achieved by providing a string-typed key/value
store on entities and groups.  This store can be used to annotate
external references to entities and groups, such as matching GitHub
users and teams.

Use of the K/V store should be carefully considered, and if you
determine you need a real directory, please consider OpenLDAP, which
is a well engineered industry standard choice for directory services.

## Ordered Keys

It is possible to order keys and values with an ordering number
appended to the key in braces.  For example, the following key/value
pairs would maintain their ordering:

```
k1{0}: these
k1{1}: are
k1{2}: ordered
```

The ordering expression is not part of the key, but is input with it
and is shown when the keys are summoned.

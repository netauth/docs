# Database

All entities and groups are stored in a key/value store.  These
key/value stores are indexed at server startup to be searchable, and
are considered an opaque storage solution.  A brief discussion of the
available storage engines follows:


## Filesystem

The filesystem backend is cross platform and will work on all
operating systems that Go can target.  It writes out keys as
individual regular files to the filesystem.  This backend is great for
getting started, but can suffer from performance problems with very
large numbers of entities or groups.

You can select this backend with the following configuration:

```toml
[db]
  backend = "filesystem"
```

## Bitcask

Bitcask is a highly performant memory mapped storage option that is
only supported on select platforms.  In general if running on a Linux
platform, this is the backend to use.  Bitcask stores the data in a
memory mapped datastore that is extremely fast up to tens of thousands
of entities and groups.

You can select this backend with the following configuration:

```toml
[db]
  backend = "bitcask"
```

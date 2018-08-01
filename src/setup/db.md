# Database

All entities and groups are stored in a database for persistence.  You
must choose what kind of database you wish to use with NetAuth.  A
discussion of available databases can be found below.

## ProtoDB

ProtoDB is the default storage engine for NetAuth.  This option will
simply use directories and files on disk to store the protocol buffers
that represent NetAuth's internal state.  This option should be
reasonably performant for many users and should scale well across
small to medium installations.

ProtoDB is safe to synchronize across multiple servers for high
availability and the disk state is consistent as much as possible, but
a crash during a write may corrupt the entity or group that was being
written, so it is recommended to backup the data directory regularly.

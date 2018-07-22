# Global Flags

Each subcommand may define its own flags which have specific meaning
within the subcommand.  The `netauth` binary itself also has flags
which have global affect.  The flags are as follows.

## Server (`--server`)

The server to connect to.  This should be either a hostname or an IP
address.  In general it should be a hostname as it is unusual to find
a certificate issued for a raw IP address.

## Port (`--port`)

The server's port.  Canonically NetAuth runs clear-text traffic on port
8080 when operating in a debug mode, it is recommended to change this
port number for production traffic.  The recommended port number is
8443.

## Client (`--client`)

The client ID is written to the server's logs to help in
troubleshooting clients that have problems.  The client ID is usually
the hostname of the system making the request, but in rare cases may
be overridden to be something else.

## Service (`--service`)

The service ID is written to the server's logs to help in
troubleshooting services that are either making too many requests, or
are otherwise not performing as expected.  In general tools that
provide NetAuth functionality will set this automatically.

## Entity (`--entity`)

The entity ID is used to uniquely identify records within NetAuth.
This is equivalent to an LDAP DN or a Kerberos Principal.  Most users
in a user-facing system will think of this as a username.  If this
value is left blank, the username of the calling user will be used
instead.

## Secret (`--secret`)

The secret that belongs to the entity specified above.  Most users
will think of this as a password.  If this value is left blank, it
will be prompted for.

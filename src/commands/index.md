# Command Reference

All management is done via the `netauth` tool.  All of the commands
have help output in the tool, but this section includes more
information and discussion about each command within the tool.

The help output for version 0.0.8.4 is as follows:

```shell
$ netauth
Usage: netauth <flags> <subcommand> <subcommand args>

Subcommands:
	commands         list all command names
	flags            describe all known top-level flags
	help             describe subcommands and their syntax

Subcommands for Authentication:
	auth             Authenticate to a NetAuth server.
	change-secret    Change the secret for a given entity
	destroy-token    Destroy an existing local token.
	get-token        Obtain a token from a NetAuth server.
	inspect-token    Inspect an existing token locally.
	validate-token   Validate an existing token with a NetAuth server.

Subcommands for Capabilities Administration:
	modify-capabilities  Modify capabilities on an entity or group

Subcommands for Entity Administration:
	entity-info      Obtain information on an entity
	modify-keys      Modify stored keys on an entity
	modify-meta      Modify meta-data on an entity
	new-entity       Add a new entity to the server
	remove-entity    Add a remove entity to the server

Subcommands for Group Administration:
	delete-group     Delete a group existing on the server.
	group-info       Obtain information on a group
	list-groups      Obtain a list of groups
	modify-group     Modify mutable fields on a group
	new-group        Add a new group to the server

Subcommands for Membership Administration:
	entity-membership  Add or remove an existing entity to an existing group
	group-expansions  Modify group expansions
	list-members     List members in a named group

Subcommands for System:
	ping             Ping a NetAuth server.


Top-level flags (use "netauth flags" for a full list):
  -server=netauth.voidlinux.org: Server Address
  -port=8443: Server port
  -client=vm2-a-lej-de: Client ID to send
  -service=netauthctl: Service ID to send
  -entity=: Entity to send in the request
  -secret=: Secret to send in the request
```

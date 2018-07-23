# Entities

Entities in NetAuth are distinct objects that can authenticate and
have meta-data.  These objects are akin to an entry in the `passwd`
database or a Kerberos principal.  Entities are generally mapped
one-to-one to human users, but can also be used for machine identity
where a machine may need access to services gated via NetAuth.

Entites are referred to in documentation in the form
`netauth/<entityID>`.

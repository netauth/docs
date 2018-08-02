# Cryptography

NetAuth stores secrets for entities.  These secrets need to be
cryptographically armored so that they can be stored with confidence.
The cryptography engines of NetAuth are implemented on a plugin
architecture, and can be chosen based on the needs of a particular
site.

Swapping cryptography systems is not supported, so choose carefully.
It is possible to build an engine that supports reencryption or
re-hashing, but the provided engines do not do this.

## bcrypt

The bcrypt engine is the only one compiled in by default.  From
Wikipedia:

> bcrypt is a password hashing function designed by Niels Provos and
> David Mazières, based on the Blowfish cipher, and presented at
> USENIX in 1999. Besides incorporating a salt to protect against
> rainbow table attacks, bcrypt is an adaptive function: over time,
> the iteration count can be increased to make it slower, so it
> remains resistant to brute-force search attacks even with increasing
> computation power.

bcrypt is the default engine and unless you have a good reason why you
should implement another cryptography engine, stick with the defaults.

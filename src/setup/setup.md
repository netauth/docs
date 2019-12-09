# Setup

Once you have installed the server, you will need to set it up.

NetAuth has a single configuration file which configures both clients
and servers.  The configuration file is handled by Viper and can be
parsed as TOML, JSON, or YAML.  TOML is the canonical format and the
format that will be shown in the documentation.

These are the defaults for the config file:

```toml
[core]
  home = ""

[crypto]
  backend = "bcrypt"

  [crypto.bcrypt]
    cost = 15

[db]
  backend = "ProtoDB"

[log]
  level = "INFO"

[pdb]
  watch-interval = "1s"
  watcher = false

[plugin]
  path = "plugins"

[server]
  bind = "localhost"
  port = 1729

[tls]
  certificate = "keys/tls.pem"
  key = "keys/tls.key"

[token]
  backend = "jwt-rsa"
  lifetime = "10m0s"

  [token.jwt]
    bits = 2048
    generate = false
```

A suitable configuration file can be as little as:

```
[core]
  home = "/var/lib/netauth"
[server]
  bind = "0.0.0.0"
```

Configuration files are resolved on a first-found basis from the
following locations:

  * $(pwd)/config.toml
  * $HOME/.netauth/config.toml
  * /etc/netauth/config.toml

It is recommended to use a job control system to run the NetAuth
server, this can be be handily done with `runit` which is available
for many distributions.  A complete `runit` service file is shown
below:

```shell
#!/bin/sh

cd /var/lib/netauthd || exit 1

exec chpst -u _netauthd:_netauthd netauthd 2>&1
```

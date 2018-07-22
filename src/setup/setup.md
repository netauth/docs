# Setup

Once you have installed the server, you will need to set it up.

The server binary (`netuathd`) has no configuration files, it is
instead configured at launch by passing flags to it.

It is recommended to use a job control system to run the NetAuth
server, this can be be handily done with `runit` which is available
for many distributions.  A complete `runit` service file is shown
below:

```shell
#!/bin/sh

cd /var/lib/netauthd || exit 1

exec chpst -u _netauthd:_netauthd netauthd \
     --bind "" \
     --port 8443 \
     --key_file security/netauth_tls_certificate.key \
     --cert_file security/netauth_tls_certificate.pem \
     --db ProtoDB \
     --protodb_root ./data \
     --crypto bcrypt \
     --bcrypt_cost 10 \
     --token_lifetime 20m \
     --token_renewals 0 \
     --token_impl jwt-rsa \
     --jwt_rsa_privatekey security/netauth_token.key \
     --jwt_rsa_publickey security/netauth_token.pem \
     2>&1
```

The above configuration should be self explanatory, but each of the
options is listed in the help output for the server.

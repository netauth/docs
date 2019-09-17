# Plugins

Plugins are a mechanism to extend the behavior of the NetAuth server.
Additional information can be read in the original [release
announcement](https://netauth.org/posts/plugged-in/).

The plugins are stored in a directory that the NetAuth server will
look at on startup, controlled by values in the `[plugin]` stanza of
the configuration file.  By default the plugins will be loaded from
`${HOME}/plugins/`, where `${HOME}` is the server's defined home
directory.

Additional values in the plugin stanza of note:

  * `enabled` - By default the plugin subsystem is enabled by default.
    If for some reason you wish to disable the plugin system set this
    value false.

  * `path` - This is the path that plugins will be searched in.  If
    this path is relative it will be computed relative to the server's
    home directory.

  * `loadstatic` - This variable controls whether or not the server
    will perform automatic discovery of plugins in teh path defined by
    the variable above.  If this is set then `list` must also be
    defined.

  * `list` - This is a list of plugins which can be loaded from the
    `path` defined above.

# Control Wireguard interfaces

* Everything related lives under `/etc/wglink`. All paths below are relative to that.
* Each managed WG interface is configured by files under `/etc/wglink/<interface>/`.
* Configuration for the node, the `[Interface]` file, is `<interface>/self.conf`.
* Each peer has its own config file under `<interface>/peers/*.conf`. Files other than `*.conf` are ignored.
  Not having any peer files is not an error.
* IP address(es) can be configured with `<interface>/ipv4` and / or `<interface>/ipv6`; the contents should be a CIDR.
  If neither exists, no IP address is assigned.
* Interfaces assumed point to point.

## The command: `wglink`

Command summary:

* `wglink list` - shows names of all interfaces managed by `wglink`.
  Note: any WG interfaces _not_ managed by `wglink` are not shown.
* `wglink create <interface>` - create an IP interface, keep it down.
  The interface must not exist, but its configuration files must be in order.
* `wglink up <interface>` - put the interface online; must be previously down.
* `wglink down <interface>` - put the interface offline; must be previously up.
* `wglink destroy <inerface>` - remove the interface; must be previously down.
* `wglink reload <interface>` - reload peer files for the interface (`wg syncconf`). The interface may be either up or down.
* `wglink status {<interface>}` - list status of given or all managed interface(s); outputs one of the following:
  * "up" - the interface is up and running;
  * "down" - the interface is configured but down;
  * "absent" - the interface is not present (e.g. not created);
  * "unknown" - the interface is not managed by `wglink`.
* `wglink help`- display this message and exit.

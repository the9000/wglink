# Control Wireguard interfaces

* Configuration for an interface is in `/etc/wg/<interface>.conf`.
* Each peer has its own config file under `/etc/wg/<interface>.peers/`.
* IP addresses assumed fixed.
* Interfaces assumed point to point.

## Wireguard interface contol command: `wglink`

* The scripts are under `/usr/local/bin`.
* `wglink up <interface>`: makes sure that the named interface is up; no-op if already up. Creates it if it's not present.
* `wglink down <interface>`: makes sure that the named interface is down; no-op if already down.
* `wglink destroy <inerface>`: destroys the interface, only if it's a Wireguard interface and is down.

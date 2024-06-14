# Prometheus OVS Exporter Snap

This repository contains the [prometheus-ovs-exporter snap](https://snapcraft.io/prometheus-ovs-exporter) package of the [Open Virtual Switch (OVS) Exporter](https://github.com/greenpau/ovs_exporter) for [Prometheus](https://prometheus.io).

## Installation

```commandline
sudo snap install prometheus-ovs-exporter
```

The snap requires privileged access to a number of system resources including the PID and unix sockets for the various OpenVSwitch processes which [cannot be granted auto-connection access](https://forum.snapcraft.io/t/allow-use-of-system-files-interface-and-auto-connection-for-prometheus-ovs-exporter-and-prometheus-ovn-exporter/32179/10).

The following commands are required to connect access to these various interfaces:

```commandline
snap connect prometheus-ovs-exporter:kernel-module-observe
snap connect prometheus-ovs-exporter:log-observe
snap connect prometheus-ovs-exporter:netlink-audit
snap connect prometheus-ovs-exporter:network-observe
snap connect prometheus-ovs-exporter:openvswitch
snap connect prometheus-ovs-exporter:etc-openvswitch
snap connect prometheus-ovs-exporter:run-openvswitch
snap connect prometheus-ovs-exporter:system-observe
```

## Configuration

The prometheus-ovs-exporter snap provides the following configuration variables that
can be set via the `snap set` command:

* __web.listenaddress__ - the IP:port to listen on, defaults to `:9475`

## Integration

The [ovn-chassis charm](https://charmhub.io/ovn-chassis) v22.09+ will automatically install and configure this snap.

v22.03 users can manually install it and configure the prometheus static-targets configuration option.

## License

This project is licensed under the terms of the Apache License 2.0. See the LICENSE file for details.


# Ansible Role: bind_exporter

An Ansible role that installs Bind Exporter on Ubuntu|Debian|Redhat-based machines with systemd|Upstart|sysvinit.

## Requirements

All required packages will be installed by this role.

## Role Variables

TODO

## Dependencies

- UnderGreen.prometheus-exporters-common

## Example Playbook

```yaml
- hosts: dns_servers
  roles:
    - role: ashleykleynhans.bind_exporter
      bind_exporter_version: 0.3.0
      bind_exporter_config_flags:
        'bind.pid-file': '/run/named/named.pid'
        'bind.stats-groups': 'server,view,tasks'
        'bind.stats-url': 'http://localhost:8053/'
        'bind.stats-version': 'auto'
        'bind.timeout': '10s'
        'web.listen-address': ':9119'
        'web.telemetry-path': '/metrics'
```

## License

GPLv2

## Author Information

Ashley Kleynhans

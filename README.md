
# Ansible Role: bind_exporter

An Ansible role that installs the Prometheus Bind Exporter Golang binary executable on Ubuntu/Debian/Redhat-based machines with systemd/Upstart/sysvinit.

## Requirements

All required packages will be installed by this role.

## Role Variables

  * bind_exporter_version : version of the Prometheus bind exporter to install from Github
  * bind.pid-file: path and filename of location pid file of the bind daemon running on the DNS server
  * bind.stats-groups: The stats that you would like to gather and export to Prometheus
  * bind.stats-url: The URL that you have exposed on your DNS server for bind stats
  * bind.stats-version: The version of bind stats
  * bind.timeout: The timeout for connecting to bind (must contatain the **s** suffix to indicate seconds)
  * web.listen-address: The TCP port to listen on for web connections
  * web.telemetry-path: The path where the metrics will be available from

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

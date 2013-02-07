# SNMP tasks Puppet Forge module

## Features

* Add an HTTP smoke test into `/etc/snmp/snmpd.conf`
* Add a file-max-age test into `/etc/snmp/snmpd.conf`

## Install

    puppet module install llehmijo/snmp_tasks

## Usage

### Monitoring HTTP services

    # In site.pp
    node "superserver" {
      # Add smoke test task for an HTTP application
      snmp_tasks::http_smoke_test { "my-web-app":
        http_port            => 80,
        smoke_test_path      => "/",
        tasks_home_directory => "/opt/monitoring-tasks"
      }
    }

The above snippet create a Bash script
`/opt/monitoring-tasks/my-web-app-http_smoke_test.sh`.
Furthermore, it will add the script into `/etc/snmp/snmpd.conf`.

## Dependencies

This Puppet module depends on
[llehmijo/snmp](https://github.com/laurilehmijoki/snmp).

## Links

This project in Puppet Forge: <http://forge.puppetlabs.com/llehmijo/snmp_tasks>.

## License

MIT

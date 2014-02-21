# Linux Hardening Role for Ansible

This role configures current best practice hardening techniques to help prevent the server from being vulnerable to common attacks. Key points addressed by this role are:

* Removing unused users & groups
* Mounting `tmpfs` as read-only
* Limit the use of `su`
* Tighten network security
* Basic `iptables` management

## Requirements

This role requires [Ansible](http://www.ansibleworks.com/) version 1.4 or higher and the Debian/Ubuntu platform.

## Role Variables

The variables that can be passed to this role and a brief description about
them are as follows:

```yaml
# The default firewall port for SSH
hardening_ssh_port: 22

# The default firewall port for MySQL
hardening_mysql_port: 3306

# The default firewall port for web traffic
hardening_webserver_ports:
  - 80
  - 443

# The default list of IPs allowed through the firewall
hardening_allowed_ips:
  - "127.0.0.1"
```

## Examples

1. Harden the server using default settings

    ```yaml
    ---
    - name: Apply hardening to all nodes
      hosts: all
      roles:
        - hardening
    ```

2. Harden the server using customized parameters

    ```yaml
    ---
    - name: Apply hardening to all nodes
      hosts: all
      roles:
        - { role: hardening
            hardening_ssh_port: "{{ openssh_port }}"
          }
    ```

## Dependencies

None.

## License

MIT.

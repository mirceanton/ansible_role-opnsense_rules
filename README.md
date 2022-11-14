OPNsense: Firewall Rules
========================

An ansible role to manage firewall rules on opnSense.

Requirements
------------

This role requires the `lxml` python package to be installed on the host system.

Role Variables
--------------

|        Variable         |     Type     |                    Description                     |
| :---------------------: | :----------: | :------------------------------------------------: |
| opnsense_firewall_rules | list(object) | List of objects that contain the rule definitions. |

See the example below for an object example.

Dependencies
------------

N/A.

Example Playbook
----------------

```yaml
- name: Configure firewall rules
  hosts: opnsense

  roles:
    - role: mirceanton.opnsense_rules
      vars:
        opnsense_firewall_rules:
          - rule:
              name: Allow LAN to Internet
              id: "2"
              _:
                - descr: Allow LAN to any
                - type: pass
                - ipprotocol: inet
                - interface: lan
                - source:
                    _:
                      - network: lan
                - destination:
                    _:
                      - any:
```

License
-------

MIT

Author Information
------------------

A role developed by [Mircea-Pavel ANTON](https://www.mirceanton.com).

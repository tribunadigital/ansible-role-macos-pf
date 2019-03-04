# Ansible Role: macos_pf

[![Build Status](https://travis-ci.org/bjoernalbers/ansible-role-macos-pf.svg?branch=master)](https://travis-ci.org/bjoernalbers/ansible-role-macos-pf)

An Ansible Role to manage the
[Packet Filter (pf)](https://en.wikipedia.org/wiki/PF_(firewall))
Firewall of macOS.

**NOTE: Currently Packet Filter will be disabled again after a reboot!**


## Requirements

The target host must be a Mac.
Also the role must be applied as root with `become: yes`.


### Role Variables

- `macos_pf_rules` (see example below)


## Dependencies

None.


## Example Playbook

```yml
---
- name: Manage Packet Filter (pf) Firewall on macOS
  hosts: macs
  # You have to become root to install the facts.
  become: yes
  roles:
    - role: macos_pf
      macos_pf_rules: |
        # Deny access to facebook for increased productivity :-)
        block drop out inet proto tcp from any to facebook.com port 443
        block drop out inet proto tcp from any to facebook.com port 80
```


## License

This Ansible role is released under the [MIT License](LICENSE.txt).

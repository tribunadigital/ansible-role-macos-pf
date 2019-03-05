# Ansible Role: macos_pf

[![Build Status](https://travis-ci.org/bjoernalbers/ansible-role-macos-pf.svg?branch=master)](https://travis-ci.org/bjoernalbers/ansible-role-macos-pf)

An Ansible Role to manage the
[Packet Filter (pf)](https://en.wikipedia.org/wiki/PF_(firewall))
Firewall of macOS.


## Requirements

These target host(s) must meet these requirements:

1. It should be a Mac, ideally with a recent version of macOS (Snow Leopard
   won't work).
2. System Integrity Protection (SIP) must temporarily be disabled.
   Otherwise the Packet Filter can't be enabled permanently across reboots.
3. You need to have access as an admin user and become "root" via `become:
   yes` - see example playbook below.


### Role Variables

Define your firewall rules with `macos_pf_rules`.


## Dependencies

None.


## Example Playbook

```yml
---
- name: Manage Packet Filter (pf) Firewall on macOS
  hosts: all
  # You have to become root to deploy the firewall rules!
  become: yes
  roles:
    - role: macos_pf
      macos_pf_rules: |
        # Block access to facebook.com for increased productivity :-)
        block drop out inet proto tcp from any to 157.240.27.35 port 443
        block drop out inet proto tcp from any to 157.240.27.35 port 80
```


## License

This Ansible role is released under the [MIT License](LICENSE.txt).

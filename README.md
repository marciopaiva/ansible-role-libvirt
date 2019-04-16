Ansible Role: libvirt
=========

[![Build Status](https://travis-ci.org/marciopaiva/ansible-role-libvirt.svg?branch=master)](https://travis-ci.org/marciopaiva/ansible-role-libvirt)
[![Ansible Galaxy](http://img.shields.io/badge/galaxy-marciopaiva.libvirt-660198.svg?style=flat)](https://galaxy.ansible.com/marciopaiva/libvirt)
[![License: GPL v3](https://img.shields.io/badge/License-GPL%20v3-blue.svg)](LICENSE)


This role install and configure a host as a Libvirt (KVM) Hypervisor.

Requirements
------------

The host should have Virtualization Technology (VT) enabled.

This role requires root access, so either run it in a playbook with a global `become: true`, or invoke the role in your playbook like:

``` yaml
- hosts: servers
  roles:
    - role: marciopaiva.libvirt
      become: true
```

Role Variables
--------------

Available variables are listed below, along with default values (see [defaults/main.yml](defaults/main.yml)):

``` yaml
---
# Whether to require that Intel Virtualisation Technology (VT) is enabled in
# order to run this role. While this provides better VM performance, it may not
# be available in certain environments.
libvirt_require_vt: true

# Default connection URI
libvirt_uri: 'qemu:///system'

# Settings for libvirt.conf configurations
libvirt_settings: []

# List of network definitions in libvirt, specified as YAML dicts.
libvirt_networks:
  - '{{ network_default }}'

# Set network default to autostart and active
network_default:
  - name: 'default'
    type: 'dnsmasq'
    bridge: 'virbr0'
    addresses:
      - '192.168.122.1/24'
    dhcp_range:
      - '2'
      - '-2'
    state: 'active'
    autostart: true
    dhcp: true
    forward: true
    
# Set pool default to autostart and active
libvirt_pools:
  - '{{ pool_default }}'

pool_default:
  - name: 'default'
    type: 'dir'
    path: '/var/lib/libvirt/images'
    state: 'active'
    autostart: true
```

Dependencies
------------

None.

Installation
------------

``` bash
$ ansible-galaxy install marciopaiva.libvirt
```

Example Playbook
----------------

``` yaml
- hosts: servers
  roles:
    - role: marciopaiva.libvirt
      become: true
```

Author Information
------------------

Marcio Paiva Barbosa.

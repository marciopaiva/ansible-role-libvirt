Role Name
=========

[![Build Status](https://travis-ci.org/marciopaiva/ansible-role-libvirt.svg?branch=master)](https://travis-ci.org/marciopaiva/ansible-role-libvirt)
[![Ansible Galaxy](http://img.shields.io/badge/galaxy-marciopaiva.libvirt-660198.svg?style=flat)](https://galaxy.ansible.com/marciopaiva/ansible-role-libvirt)
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

A description of the settable variables for this role.

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

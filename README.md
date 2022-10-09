Ansible Role: Teleport
=========

This role will deploy teleport to a given server. 

What this does
---------------

You can configure which parts of a teleport deployment you want with variables.

- Install teleport via DEB/RPM with GPG check
- Install teleport from tarball with GPG check (None apt/rpm systems)
- Enroll automatically as a node for SSH

Requirements
------------

A system running utilizing systemd
This has only been tested on:

Debian 10/11
RHEL 7/8/9
openSUSE 15.0/1/2/3/Tumbleweed


Role Variables
--------------

### Group Vars:

| Name           | Type    | Example           |
|----------------|---------|-------------------|
| INVITE_TOKEN   | string  | 4f622402dawdawdaw |
| CA_PIN         | string  | sha256:2awdwadwad678767awd768awdd |
| TELEPORT_HOST  | string  | teleport.domain.tld:443 |
| TELEPORT_MAJOR_VERSION | INT | 10 |
| TELEPORT_MINOR_VERSION | FLOAT | 3.1 |



### Host Vars:

| Name   | Type    |  Example    |
|--------|---------|-------------|
| SSH_SERVICE | string | yes     |

Dependencies
------------

There are no dependencies for this role

Example Playbook
----------------

PLAYBOOK:
```yaml
- hosts: teleport
  become: true
  roles:
    - jamdoog.teleport
  vars:
    - INVITE_TOKEN: ...
    - CA_PIN: ...
    - TELEPORT_HOST: ...
    - TELEPORT_MINOR_VERSION: ...
    - TELEPORT_MAJOR_VERSION: ...
    - SSH_SERVICE: ...
    
```

License
-------

BSD

Author Information
------------------

This role was created by James Ledger, I write about things on https://jamesledger.net
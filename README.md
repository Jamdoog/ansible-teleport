Ansible Role: Teleport
=========

This role will deploy teleport to a given server. 

What this does
---------------

You can configure which parts of a teleport deployment you want with variables.

- Install teleport via DEB/RPM with GPG check
- Install teleport from tarball with GPG check (None apt/rpm systems)
- Enroll automatically as a node for SSH
- Automatically deploy "commands"/labels for SSH and Application such as Kernel, Teleport & more versioning.

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
| TELEPORT_MINOR_VERSION | FLOAT | 3.2 |



### Host Vars:

| Name   | Type    |  Example    |
|--------|---------|-------------|
| SSH_SERVICE | bool | true    |
| APP_SERVICE | bool | true |
| CREATE_SSH_COMMANDS | bool | true |
| CREATE_APP_COMMANDS | bool | true |
| CREATE_COMMANDS | bool | true |
| CREATE_OS_COMMANDS | bool | true |
| CREATE_KERNEL_COMMANDS | bool | true |
| CREATE_TELEPORT_COMMANDS | bool | true |
| TELEPORT_APPLICATION_NAME | string | proxmox |
| TELEPORT_APPLICATION_IGNORE_TLS | string | true |
| TELEPORT_APPLICATION_URI | string | https://192.168.200.1:8006  |



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
    - INVITE_TOKEN: 4f622402dawdawdaw
    - CA_PIN: sha256:2awdwadwad678767awd768awdd
    - TELEPORT_HOST: domain.tld:443
    - TELEPORT_MINOR_VERSION: 3.2
    - TELEPORT_MAJOR_VERSION: 10
    - SSH_SERVICE: true
    - APP_SERVICE: true
    - CREATE_COMMANDS: true 
    - CREATE_HOSTNAME_COMMAND: true 
    - CREATE_OS_COMMAND: true
    - CREATE_KERNEL_COMMAND: true
    - CREATE_TELEPORT_COMMAND: true
    - TELEPORT_APPLICATION_NAME: "proxmox"
    - TELEPORT_APPLICATION_IGNORE_TLS: true
    - TELEPORT_APPLICATION_URI: "https://192.168.200.1:8006"

    
```

License
-------

BSD

Author Information
------------------

This role was created by James Ledger, I write about things on https://jamesledger.net
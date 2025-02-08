os-upgrade
==========
[![Ansible Lint](https://github.com/oxivanisher/role-os_upgrade/actions/workflows/ansible-lint.yml/badge.svg)](https://github.com/oxivanisher/role-os_upgrade/actions/workflows/ansible-lint.yml)

Upgrades all OS packages to the latest version.
If the `os_upgrade_octoprint_api_key` variable is set, it checks for running 3d prints and excludes the system from updates if it is printing.

Role Variables
--------------

| Name                         | Comment                                   | Default value |
|------------------------------|-------------------------------------------|---------------|
| os_upgrade_octoprint_api_key | Octoprint API key                         | ``            |


Dependencies
------------

None

Example Playbook
----------------

```yaml
- name: Raspberry Pi
  hosts: all
  collections:
    - oxivanisher.linux_base
  roles:
    - role: oxivanisher.linux_base.os_upgrade              # upgrade all packages
```

License
-------

BSD

Author Information
------------------

This role is part of the [oxivanisher.linux_base](https://galaxy.ansible.com/ui/repo/published/oxivanisher/linux_base/) collection, and the source for that is located on [github](https://github.com/oxivanisher/collection-linux_base).

os-upgrade
==========
[![Ansible Lint](https://github.com/oxivanisher/role-os_upgrade/actions/workflows/ansible-lint.yml/badge.svg)](https://github.com/oxivanisher/role-os_upgrade/actions/workflows/ansible-lint.yml)

Upgrades all OS packages to the latest version with support for Debian/Ubuntu, Red Hat/CentOS, and Suse/SLES systems.

Features
--------

* **Multi-OS Support**: Debian, Ubuntu, Red Hat, CentOS, and Suse/SLES
* **3D Print Detection**: Checks OctoPrint API for active prints and skips upgrades when printing
* **Smart Reboot Management**: Detects when reboots are needed and optionally performs them automatically
* **Pushover Notifications**: Sends notifications before rebooting (when configured)
* **Package Cleanup**: Removes unused dependencies and clears package caches

Role Variables
--------------

| Name                           | Comment                                                                                                                                                            | Default value |
| ------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------- |
| os_upgrade_clean_package_files | Should all downloaded package file be removed after upgrades where installed?                                                                                      | `true`        |
| os_upgrade_debian_mode         | Select the [package upgrade mode](https://docs.ansible.com/ansible/latest/collections/ansible/builtin/apt_module.html)                                             | `dist`        |
| os_upgrade_do_reboot           | Should the systems always be rebooted?                                                                                                                             | `false`       |
| os_upgrade_octoprint_api_key   | Octoprint API key                                                                                                                                                  | ``            |
| os_upgrade_pushover_appkey     | Pushover app key for reboot notification                                                                                                                           | ``            |
| os_upgrade_pushover_userkey    | Pushover user key for reboot notification                                                                                                                          | ``            |
| os_upgrade_reboot_if_required  | Only reboot the system if it is required.                                                                                                                          | `false`       |
| os_upgrade_suse_force_accept   | This forces zypper to accept new repo keys, replace files during upgrades and allows vendor changes.                                                               | `true`        |
| os_upgrade_suse_mode           | Select the target [package state](https://docs.ansible.com/ansible/latest/collections/community/general/zypper_module.html). Should be `latest` or `dist-upgrade`. | `latest`      |


**A note to reboot:** This variable controls if the system(s) will be rebooted. Default is no reboot, change `os_upgrade_do_reboot` to `true` to force reboots.


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
